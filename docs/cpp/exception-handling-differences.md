---
title: Behandeln strukturierter Ausnahmen in C++
description: Behandelt strukturierte Ausnahmen mithilfe des C++-Ausnahme Behandlungs Modells.
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0f92bbe64db028ec6a7fd6ae2cc217c707d3e2c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221587"
---
# <a name="handle-structured-exceptions-in-c"></a>Behandeln strukturierter Ausnahmen in C++

Der Hauptunterschied zwischen der c-strukturierten Ausnahmebehandlung (SEH) und der C++-Ausnahmebehandlung besteht darin, dass das C++-Ausnahme Behandlungsmodell Typen behandelt, während das C-strukturierte Ausnahme Behandlungsmodell Ausnahmen von einem Typ behandelt. insbesondere **`unsigned int`** . Das bedeutet, dass C-Ausnahmen über einen Ganzzahlwert ohne Vorzeichen identifiziert werden und C++-Ausnahmen über den Datentyp. Wenn eine strukturierte Ausnahme in C ausgelöst wird, führt jeder mögliche Handler einen Filter aus, der den C-Ausnahme Kontext untersucht und bestimmt, ob die Ausnahme akzeptiert, an einen anderen Handler übergeben oder ignoriert werden soll. Wenn eine Ausnahme in C++ ausgelöst wird, kann sie einem beliebigen Typ angehören.

Ein zweiter Unterschied besteht darin, dass das Modell für die strukturierte Ausnahmebehandlung in C als *asynchron*bezeichnet wird, da Ausnahmen für die normale Ablauf Steuerung Sekundär vorkommen. Der C++-Ausnahme Behandlungs Mechanismus ist vollständig *synchron*, was bedeutet, dass Ausnahmen nur auftreten, wenn Sie ausgelöst werden.

Wenn Sie die [/EHS-oder/EHsc](../build/reference/eh-exception-handling-model.md) -Compileroption verwenden, behandeln keine C++-Ausnahmehandler strukturierte Ausnahmen. Diese Ausnahmen werden nur von **`__except`** strukturierten Ausnahme Handlern oder strukturierten Beendigungs **`__finally`** Handlern behandelt. Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung (C/C++)](structured-exception-handling-c-cpp.md).

Wenn eine C-Ausnahme in einem C++-Programm ausgelöst wird, kann Sie unter der [/EHa](../build/reference/eh-exception-handling-model.md) -Compileroption von einem strukturierten Ausnahmehandler mit dem zugehörigen Filter oder einem C++-Handler behandelt werden **`catch`** , je nachdem, welcher Vorgang sich dynamisch an den Ausnahme Kontext nähert. Beispielsweise löst das C++-Beispielprogramm in einem C++-Kontext eine C-Ausnahme aus **`try`** :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Beispiel: Abfangen einer C-Ausnahme in einem C++ catch-Block

```cpp
// exceptions_Exception_Handling_Differences.cpp
// compile with: /EHa
#include <iostream>

using namespace std;
void SEHFunc( void );

int main() {
   try {
      SEHFunc();
   }
   catch( ... ) {
      cout << "Caught a C exception."<< endl;
   }
}

void SEHFunc() {
   __try {
      int x, y = 0;
      x = 5 / y;
   }
   __finally {
      cout << "In finally." << endl;
   }
}
```

```Output
In finally.
Caught a C exception.
```

## <a name="c-exception-wrapper-classes"></a>Wrapper Klassen für C-Ausnahmen

In einem einfachen Beispiel wie oben kann die C-Ausnahme nur durch Auslassungs Punkte (**...**) **`catch`** abgefangen werden. lers. Es werden keine Informationen über den Typ oder die Art der Ausnahme an den Handler übermittelt. Diese Methode funktioniert zwar, in einigen Fällen möchten Sie jedoch möglicherweise eine Transformation zwischen den beiden Ausnahme Behandlungs Modellen definieren, damit jede C-Ausnahme einer bestimmten Klasse zugeordnet ist. Um einen zu transformieren, können Sie eine Wrapper Klasse der c-Ausnahme definieren, die verwendet oder abgeleitet werden kann, um einer C-Ausnahme einen bestimmten Klassentyp zuzuordnen. Auf diese Weise kann jede C-Ausnahme separat von einem bestimmten C++-Handler behandelt werden **`catch`** , und nicht von allen in einem einzigen Handler.

Die Wrapperklasse enthält eventuell eine Schnittstelle, die aus mehreren Memberfunktionen besteht, die den Wert der Ausnahme bestimmen und auf die erweiterten Ausnahmekontextinformationen zugreifen, die vom C-Ausnahmemodell bereitgestellt werden. Möglicherweise möchten Sie auch einen Standardkonstruktor und einen Konstruktor definieren, der ein **`unsigned int`** Argument annimmt (um die zugrunde liegende C-Ausnahme Darstellung bereitzustellen) und einen bitweisen Kopierkonstruktor. Hier ist eine mögliche Implementierung einer Wrapper Klasse für eine C-Ausnahme:

```cpp
// exceptions_Exception_Handling_Differences2.cpp
// compile with: /c
class SE_Exception {
private:
   SE_Exception() {}
   SE_Exception( SE_Exception& ) {}
   unsigned int nSE;
public:
   SE_Exception( unsigned int n ) : nSE( n ) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() {
      return nSE;
   }
};
```

Wenn Sie diese Klasse verwenden möchten, installieren Sie eine benutzerdefinierte C-Ausnahme Übersetzungsfunktion, die bei jedem Auslösen einer C-Ausnahme vom internen Mechanismus zur Ausnahmebehandlung aufgerufen wird. In ihrer Übersetzungsfunktion können Sie eine beliebige typisierte Ausnahme auslösen (z. a. einen `SE_Exception` Typ oder einen von abgeleiteten Klassentyp `SE_Exception` ), der von einem entsprechenden passenden C++-Handler abgefangen werden kann **`catch`** . Die Übersetzungsfunktion kann stattdessen zurückgeben, was darauf hinweist, dass die Ausnahme nicht behandelt wurde. Wenn die Übersetzungsfunktion selbst eine C-Ausnahme auslöst, wird [Beenden](../c-runtime-library/reference/terminate-crt.md) aufgerufen.

Um eine benutzerdefinierte Übersetzungsfunktion anzugeben, nennen Sie die [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) -Funktion mit dem Namen Ihrer Übersetzungsfunktion als einzelnes Argument. Die Übersetzungsfunktion, die Sie schreiben, wird einmal für jeden Funktionsaufruf auf dem Stapel mit- **`try`** Blöcken aufgerufen. Es ist keine Standard Übersetzungsfunktion vorhanden. Wenn Sie keinen angeben, indem Sie **_set_se_translator**aufrufen, kann die C-Ausnahme nur von einem Ellipsen Handler abgefangen werden **`catch`** .

## <a name="example---use-a-custom-translation-function"></a>Beispiel: Verwenden einer benutzerdefinierten Übersetzungsfunktion

Der folgende Code installiert beispielsweise eine benutzerdefinierte Übersetzungsfunktion und löst anschließend eine C-Ausnahme aus, die von der `SE_Exception`-Klasse umschlossen wird:

```cpp
// exceptions_Exception_Handling_Differences3.cpp
// compile with: /EHa
#include <stdio.h>
#include <eh.h>
#include <windows.h>

class SE_Exception {
private:
   SE_Exception() {}
   unsigned int nSE;
public:
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}
   SE_Exception(unsigned int n) : nSE(n) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() { return nSE; }
};

void SEFunc() {
    __try {
        int x, y = 0;
        x = 5 / y;
    }
    __finally {
        printf_s( "In finally\n" );
    }
}

void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {
    printf_s( "In trans_func.\n" );
    throw SE_Exception( u );
}

int main() {
    _set_se_translator( trans_func );
    try {
        SEFunc();
    }
    catch( SE_Exception e ) {
        printf_s( "Caught a __try exception with SE_Exception.\n" );
        printf_s( "nSE = 0x%x\n", e.getSeNumber() );
    }
}
```

```Output
In trans_func.
In finally
Caught a __try exception with SE_Exception.
nSE = 0xc0000094
```

## <a name="see-also"></a>Weitere Informationen

[Kombination von C-Ausnahmen (strukturiert) und C++-Ausnahmen](../cpp/mixing-c-structured-and-cpp-exceptions.md)
