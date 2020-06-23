---
title: 'Funktions Aufrufoperator: ()'
ms.date: 06/11/2020
helpviewer_keywords:
- ( ) function call operator
- function calls, C++ functions
- () function call operator
- postfix operators [C++]
- function calls, operator
- functions [C++], function-call operator
- function call operator ()
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
no-loc:
- opt
ms.openlocfilehash: 59fd36a5ae135c55813019f04b0f5df4be2800b3
ms.sourcegitcommit: 2d7550d0f375aafa428ef0fb2e3962e4232be28e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "84777304"
---
# <a name="function-call-operator-"></a>Funktionsaufrufoperator: ()

Ein Funktions aufzurufen ist eine Art von *`postfix-expression`* , die durch einen Ausdruck gebildet wird, der eine Funktion, gefolgt vom Funktions aufrufsoperator, angibt **`()`** . Ein-Objekt kann eine-Funktion deklarieren `operator ()` , die Funktions Aufrufsemantik für das-Objekt bereitstellt.

## <a name="syntax"></a>Syntax

> *`postfix-expression`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;*`postfix-expression`* **`(`** *`argument-expression-list`* <sub>opt</sub> **`)`**

## <a name="remarks"></a>Hinweise

Die Argumente für den Funktions Aufrufoperator stammen aus einer *`argument-expression-list`* , einer durch Trennzeichen getrennten Liste von Ausdrücken. Die Werte dieser Ausdrücke werden als Argumente an die Funktion übermittelt. Die *Argument-Expression-List* kann leer sein. Vor C++ 17 ist die Reihenfolge der Auswertung des Funktions Ausdrucks und der Argument Ausdrücke nicht angegeben und kann in beliebiger Reihenfolge auftreten. In c++ 17 und höher wird der Funktions Ausdruck vor allen Argument Ausdrücken oder Standardargumenten ausgewertet. Die Argument Ausdrücke werden in einer unbestimmten Reihenfolge ausgewertet.

Der *`postfix-expression`* identifiziert die aufzurufende Funktion. Es muss zu einer Funktions Adresse ausgewertet werden. Sie kann verschiedene Formen annehmen:

- ein Funktions-oder Funktions Objektname oder-Zeiger,
- ein Lvalue-Ausdruck, der auf ein Funktions-oder Funktions Objekt verweist.
- ein Element Funktions Accessor, entweder explizit oder implizit.

Die von angegebene Funktion *`postfix-expression`* kann eine überladene Funktion sein. Die üblichen Regeln für die Überladungs Auflösung bestimmen die tatsächlich aufzurufende Funktion.

Einige Beispiel Deklarationen:

- Funktion, die den Typ `T` zurückgibt. Eine Beispieldeklaration ist

    ```cpp
    T func( int i );
    ```

- Zeiger auf eine Funktion, die den Typ `T` zurückgibt. Eine Beispieldeklaration ist

    ```cpp
    T (*func)( int i );
    ```

- Verweis auf eine Funktion, die den Typ `T` zurückgibt. Eine Beispieldeklaration ist

    ```cpp
    T (&func)(int i);
    ```

- Zeiger auf eine Memberfunktion dereferenziert die Rückgabe des Typs `T`. Beispiele für Funktionsaufrufe sind

    ```cpp
    (pObject->*pmf)();
    (Object.*pmf)();
    ```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Standardbibliotheksfunktion `strcat_s` mit drei Argumenten aufgerufen:

```cpp
// expre_Function_Call_Operator.cpp
// compile with: /EHsc

#include <iostream>
#include <string>

// C++ Standard Library name space
using namespace std;

int main()
{
    enum
    {
        sizeOfBuffer = 20
    };

    char s1[ sizeOfBuffer ] = "Welcome to ";
    char s2[ ] = "C++";

    strcat_s( s1, sizeOfBuffer, s2 );

    cout << s1 << endl;
}
```

```Output
Welcome to C++
```

## <a name="function-call-results"></a>Ergebnisse des Funktionsaufrufs

Ein Funktions Aufrufwert wird zu einem Rvalue ausgewertet, es sei denn, die Funktion wird als Verweistyp deklariert. Funktionen mit Verweis Rückgabe Typen werden als Lvalues ausgewertet. Diese Funktionen können auf der linken Seite einer Zuweisungsanweisung verwendet werden, wie hier zu sehen ist:

```cpp
// expre_Function_Call_Results.cpp
// compile with: /EHsc
#include <iostream>
class Point
{
public:
    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
private:
    unsigned _x;
    unsigned _y;
};

using namespace std;
int main()
{
    Point ThePoint;

    ThePoint.x() = 7;           // Use x() as an l-value.
    unsigned y = ThePoint.y();  // Use y() as an r-value.

    // Use x() and y() as r-values.
    cout << "x = " << ThePoint.x() << "\n"
         << "y = " << ThePoint.y() << "\n";
}
```

Der vorangehende Code definiert eine Klasse `Point` mit dem Namen, die private Datenobjekte enthält, die *x* -und *y* -Koordinaten darstellen. Diese Datenobjekte müssen geändert und ihre Werte abgerufen werden. Dieses Programm ist nur einer von mehreren Entwürfen für eine solche Klasse. Eine Verwendung der Funktionen `GetX` und `SetX` oder `GetY` und `SetY` ist ein anderer möglicher Entwurf.

Funktionen, die Klassentypen, Zeiger auf Klassentypen oder Verweise auf Klassentypen zurückgeben, können als linker Operand für Memberauswahloperatoren verwendet werden. Der folgende Code ist zulässig:

```cpp
// expre_Function_Results2.cpp
class A {
public:
   A() {}
   A(int i) {}
   int SetA( int i ) {
      return (I = i);
   }

   int GetA() {
      return I;
   }

private:
   int I;
};

A func1() {
   A a = 0;
   return a;
}

A* func2() {
   A *a = new A();
   return a;
}

A& func3() {
   A *a = new A();
   A &b = *a;
   return b;
}

int main() {
   int iResult = func1().GetA();
   func2()->SetA( 3 );
   func3().SetA( 7 );
}
```

Funktionen können rekursiv aufgerufen werden. Weitere Informationen zu Funktions Deklarationen finden Sie unter [Functions](functions-cpp.md). Verwandte Materialien sind [Übersetzungseinheiten und Verknüpfungen](../cpp/program-and-linkage-cpp.md).

## <a name="see-also"></a>Weitere Informationen

[Postfixausdrücke](../cpp/postfix-expressions.md)<br/>
[C++ integrierte Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Funktionsaufruf](../c-language/function-call-c.md)
