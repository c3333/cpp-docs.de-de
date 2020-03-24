---
title: Zuweisung
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: f1697a8de3dff6c46de01db6bbff5447c03b6282
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190702"
---
# <a name="assignment"></a>Zuweisung

Der Zuweisungs Operator ( **=** ) ist, streng genommen, ein binärer Operator. Seine Deklaration ist mit jedem anderen binären Operator identisch, mit den folgenden Ausnahmen:

- Es muss eine nicht statische Memberfunktion sein. No **Operator =** kann als nicht-Member-Funktion deklariert werden.
- Es wird nicht von abgeleiteten Klassen geerbt.
- Eine Standard **Operator =** -Funktion kann vom Compiler für Klassentypen generiert werden, sofern keine vorhanden ist.

Das folgende Beispiel veranschaulicht, wie Sie einen Zuweisungsoperator deklarieren:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

Das angegebene Argument ist die Rechte Seite des Ausdrucks. Der Operator gibt das Objekt zurück, um das Verhalten des Zuweisungsoperators beizubehalten, der den Wert des linken Rands zurückgibt, nachdem die Zuweisung abgeschlossen ist. Dies ermöglicht die Verkettung von Zuweisungen, wie z. b.:

```cpp
pt1 = pt2 = pt3;
```

Der Kopier Zuweisungs Operator muss nicht mit dem Kopierkonstruktor verwechselt werden. Letzteres wird während der Erstellung eines neuen Objekts aus einer vorhandenen aufgerufen:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Es empfiehlt sich, der [Regel drei](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) zu folgen, dass eine Klasse, die einen Kopier Zuweisungs Operator definiert, auch den Kopierkonstruktor, Dekonstruktor und, beginnend mit c++ 11, den Konstruktor-und den Verschiebungs Zuweisungs Operator explizit definieren sollte.

## <a name="see-also"></a>Weitere Informationen

- [Operatorüberladung](../cpp/operator-overloading.md)
- [Kopierkonstruktoren und Kopierzuweisungsoperatoren (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
