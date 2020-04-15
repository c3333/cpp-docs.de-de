---
title: Überladen von Inkrementierungs- und Dekrementierungsoperatoren (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 40ae12130fdced9fd958c3b8316fa3b718ca9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374131"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Überladen von Inkrementierungs- und Dekrementierungsoperatoren (C++)

Die Inkrement- und Dekrementoperatoren gehören einer speziellen Kategorie an, da es jeweils zwei Varianten gibt:

- Präinkrement und Postinkrement

- Prädekrement und Postdekrement

Wenn Sie überladene Operator-Funktionen schreiben, kann es hilfreich sein, separate Versionen für die Präfix- und Postfix-Versionen dieser Operatoren zu implementieren. Um zwischen den beiden zu unterscheiden, wird die folgende Regel beachtet: Die Präfixform des Operators wird genau auf die gleiche Weise deklariert wie jeder andere unäre Operator; Das postfix-Formular akzeptiert ein zusätzliches Argument vom Typ **int**.

> [!NOTE]
> Wenn Sie einen überladenen Operator für die Postfixform des Inkrement- oder Dekrementoperators angeben, muss das zusätzliche Argument vom Typ **int**sein. Wenn Sie einen anderen Typ angeben, wird ein Fehler generiert.

Das folgende Beispiel zeigt, wie Präfix- und Postfix-Inkrement- und Dekrementoperatoren für die Klasse `Point` definiert werden:

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

Die gleichen Operatoren können im Dateigültigkeitsbereich (global) mit den folgenden Funktionsköpfen definiert werden:

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

Das Argument vom Typ **int,** das die Postfixform des Inkrement- oder Dekrementoperators bezeichnet, wird nicht häufig zum Übergeben von Argumenten verwendet. Es enthält in der Regel den Wert 0. Es kann jedoch wie folgt verwendet werden:

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

Es gibt keine Syntax für die Verwendung von Inkrement- oder Dekrementoperatoren, um diese Werte auf eine andere Weise zu übertragen als durch expliziten Aufruf, wie im vorangehenden Code dargestellt. Eine einfachere Möglichkeit, diese Funktionalität zu implementieren, besteht**+=** darin, den Additions-/Zuweisungsoperator ( ) zu überlasten.

## <a name="see-also"></a>Siehe auch

[Operatorüberladung](../cpp/operator-overloading.md)
