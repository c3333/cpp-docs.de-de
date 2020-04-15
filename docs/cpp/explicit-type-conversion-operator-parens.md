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
ms.openlocfilehash: c168653a82b4d4c5023de1f76a1e6269625c74d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354859"
---
# <a name="explicit-type-conversion-operator-"></a>Operator für die explizite Typkonvertierung: ()

C++ lässt die explizite Typkonvertierung mithilfe der Syntax ähnlich der Syntax des Funktionsaufrufs zu.

## <a name="syntax"></a>Syntax

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Bemerkungen

Ein *einfacher Typname* gefolgt von einer *Ausdrucksliste,* die in Klammern eingeschlossen ist, erstellt ein Objekt des angegebenen Typs mithilfe der angegebenen Ausdrücke. Das folgende Beispiel zeigt eine explizite Typkonvertierung in den Typ "int":

```cpp
int i = int( d );
```

Das folgende Beispiel `Point` zeigt eine Klasse.

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

Obwohl das obige Beispiel die explizite Typkonvertierung mithilfe von Konstanten demonstriert, funktioniert das gleiche Verfahren, um diese Konvertierungen für Objekte auszuführen. Der folgende Codeausschnitt stellt dies dar:

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

Das obige Beispiel, das die Konvertierung im Funktionsstil verwendet, zeigt, wie zwei Werte (einer für *x* und einer für *y*) in den benutzerdefinierten Typ `Point`konvertiert werden.

> [!CAUTION]
> Verwenden Sie die expliziten Typkonvertierungen mit Bedacht, da sie die integrierte Typüberprüfung des C++-Compilers überschreiben.

Die [Umwandlungsnotation](../cpp/cast-operator-parens.md) muss für Konvertierungen in Typen verwendet werden, die keinen *einfachen Typnamen* haben (z. B. Zeiger- oder Verweistypen). Konvertierung in Typen, die mit einem *einfachen Typnamen* ausgedrückt werden können, kann in beiden Formen geschrieben werden.

Eine Typdefinition innerhalb von Umwandlungen ist unzulässig.

## <a name="see-also"></a>Siehe auch

[Postfixausdrücke](../cpp/postfix-expressions.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
