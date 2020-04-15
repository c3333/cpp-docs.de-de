---
title: Grundlegende Konzepte zur Verwendung verwalteter Ausnahmen
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372527"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Grundlegende Konzepte zur Verwendung verwalteter Ausnahmen

In diesem Thema wird die Ausnahmebehandlung in verwalteten Anwendungen behandelt. Das heißt, eine Anwendung, die mit der Compileroption **/clr** kompiliert wird.

## <a name="in-this-topic"></a>In diesem Thema

- [Auslösen von Ausnahmen unter /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Try/Catch-Blöcke für CLR-Erweiterungen](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Bemerkungen

Wenn Sie mit der Option **/clr** kompilieren, können <xref:System.Exception> Sie CLR-Ausnahmen verarbeiten, sowie standardklasse bietet viele nützliche Methoden für die Verarbeitung von CLR-Ausnahmen und wird als Basisklasse für benutzerdefinierte Ausnahmeklassen empfohlen.

Das Abfangen von Ausnahmetypen, die von einer Schnittstelle abgeleitet werden, wird unter **/clr**nicht unterstützt. Außerdem können Sie aufgrund der Common Language Runtime keine Stackoverflow-Ausnahmen abfangen. Eine Stapelüberlaufausnahme beendet den Prozess.

Weitere Informationen zu Unterschieden in der Ausnahmebehandlung in verwalteten und nicht verwalteten Anwendungen finden Sie unter [Unterschiede im Verhalten der Ausnahmebehandlung unter Verwaltete Erweiterungen für C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Auslösen von Ausnahmen unter /clr

Der C++-Throw-Ausdruck wird erweitert, um ein Handle in einen CLR-Typ zu werfen. Im folgenden Beispiel wird ein benutzerdefinierter Ausnahmetyp erstellt und dann eine Instanz dieses Typs ausgelöst:

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

Ein Werttyp muss vor dem Auswerfen geschachtelt werden:

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/Catch-Blöcke für CLR-Erweiterungen

Die gleiche **try**/**catch-Blockstruktur** kann zum Abfangen von CLR- und systemeigenen Ausnahmen verwendet werden:

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>Output

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Reihenfolge des Abwickelns für C++-Objekte

Das Entladen erfolgt für alle C++-Objekte mit Destruktoren, die sich möglicherweise auf dem Laufzeitstapel zwischen der Auswerfen-Funktion und der Handling-Funktion befinden. Da CLR-Typen auf dem Heap zugewiesen sind, gilt das Entladen nicht für sie.

Die Reihenfolge der Ereignisse für eine ausgelöste Ausnahme ist wie folgt:

1. Die Laufzeit führt den Stapel auf der Suche nach der entsprechenden catch-Klausel, oder im Fall von SEH, einem Ausnahmefilter für SEH, um die Ausnahme abzufangen. Catch-Klauseln werden zuerst in lexikalischer Reihenfolge und dann dynamisch in der Aufrufliste durchsucht.

1. Sobald der richtige Handler gefunden wurde, wird der Stapel bis zu diesem Punkt aufgelöst. Für jeden Funktionsaufruf im Stapel werden die lokalen Objekte zerstört und __finally Blöcke ausgeführt, von den meisten nach außen verschachtelt.

1. Sobald der Stapel aufgelöst wurde, wird die catch-Klausel ausgeführt.

### <a name="catching-unmanaged-types"></a>Nicht verwaltete Typen fangen

Wenn ein nicht verwalteter Objekttyp ausgelöst wird, <xref:System.Runtime.InteropServices.SEHException>wird er mit einer Ausnahme vom Typ umbrochen. Bei der Suche nach der geeigneten **Fangklausel** gibt es zwei Möglichkeiten.

- Wenn ein systemeigener C++-Typ gefunden wird, wird die Ausnahme entpackt und mit dem gefundenen Typ verglichen. Mit diesem Vergleich kann ein systemeigener C++-Typ auf die normale Weise abgefangen werden.

- Wenn jedoch zuerst eine **catch-Klausel** vom Typ **SEHException** oder eine ihrer Basisklassen untersucht wird, fängt die Klausel die Ausnahme ab. Daher sollten Sie alle catch-Klauseln platzieren, die systemeigene C++-Typen fangen, zuerst vor catch-Klauseln von CLR-Typen.

Beachten Sie Folgendes:

```
catch(Object^)
```

and

```
catch(...)
```

werden beide ausgelöste Typen einschließlich SEH-Ausnahmen abgefangen.

Wenn ein nicht verwalteter Typ von catch(Object) abgefangen wird, wird das ausgelöste Objekt nicht zerstört.

Beim Auslösen oder Abfangen nicht verwalteter Ausnahmen wird empfohlen, die Compileroption [/EHsc](../build/reference/eh-exception-handling-model.md) anstelle von **/EHs** oder **/EHa**zu verwenden.

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[Safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md)
