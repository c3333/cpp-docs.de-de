---
title: 'Operator für die explizite Typkonvertierung: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: 079a3390df56ba55bd4d71a320faa249266abb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189012"
---
# <a name="explicit-type-conversion-operator-"></a>Operator für die explizite Typkonvertierung: ()

C++ lässt die explizite Typkonvertierung mithilfe der Syntax ähnlich der Syntax des Funktionsaufrufs zu.

## <a name="syntax"></a>Syntax

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Bemerkungen

Ein *Simple-Type-Name* , gefolgt von einer in Klammern eingeschlossenen *Ausdrucks Liste, erstellt* mithilfe der angegebenen Ausdrücke ein Objekt vom angegebenen Typ. Das folgende Beispiel zeigt eine explizite Typkonvertierung in den Typ "int":

```cpp
int i = int( d );
```

Das folgende Beispiel zeigt eine `Point`-Klasse.

## <a name="example"></a>Beispiel

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>Output

```Output
x = 20, y = 10
x = 0, y = 0
```

Obwohl das obige Beispiel die explizite Typkonvertierung mithilfe von Konstanten demonstriert, funktioniert das gleiche Verfahren, um diese Konvertierungen für Objekte auszuführen. Dies wird im folgenden Codefragment dargestellt:

```cpp
int i = 7;
float d;

d = float( i );
```

Explizite Typkonvertierungen können mithilfe der "cast"-Syntax ebenfalls angegeben werden. Das vorherige Beispiel, das mithilfe der Umwandlungssyntax neu geschrieben wird, lautet:

```cpp
d = (float)i;
```

Umwandlungs- und Funktionskonvertierungen haben dieselben Ergebnisse beim Konvertieren von Einzelwerten. In der Funktionsformatsyntax können Sie mehr als ein Argument für die Konvertierung angeben. Dieser Unterschied ist für benutzerdefinierte Typen wichtig. Betrachten Sie eine `Point`-Klasse und ihre Konvertierungen:

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

Im vorherigen Beispiel, in dem die Funktionsweise Konvertierung verwendet wird, wird veranschaulicht, wie zwei Werte (eine für *x* und eine für *y*) in den benutzerdefinierten Typ `Point`konvertiert werden.

> [!CAUTION]
>  Verwenden Sie die expliziten Typkonvertierungen mit Bedacht, da sie die integrierte Typüberprüfung des C++-Compilers überschreiben.

Die [Cast](../cpp/cast-operator-parens.md) Notation muss für Konvertierungen in Typen verwendet werden, die nicht über einen *einfachen Typnamen* (z. b. Zeiger-oder Verweis Typen) verfügen. Die Konvertierung in Typen, die mit einem *Simple-Type-Name* ausgedrückt werden können, kann in beide Formen geschrieben werden.

Eine Typdefinition innerhalb von Umwandlungen ist unzulässig.

## <a name="see-also"></a>Weitere Informationen

[Postfixausdrücke](../cpp/postfix-expressions.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
