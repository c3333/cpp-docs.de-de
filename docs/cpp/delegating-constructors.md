---
title: Delegieren von Konstruktoren (C++)
description: Verwenden Sie delegierende Konstruktoren in C++, um andere Konstruktoren aufzurufen und die Codewiederholung zu reduzieren.
ms.date: 11/19/2019
ms.openlocfilehash: f26a013aa3c081d900ffc3eb32649acc77505db0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316673"
---
# <a name="delegating-constructors"></a>Delegierende Konstruktoren

Viele Klassen verfügen über mehrere Konstruktoren, die ähnliche Aufgaben ausführen, beispielsweise Parameter überprüfen:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Sie können Codewiederholungen reduzieren, indem Sie eine Funktion hinzufügen, die die gesamte Validierung übernimmt. Der Code für `class_c` wäre jedoch einfacher zu verstehen und zu verwalten, wenn ein Konstruktor einen Teil der Aufgaben an einen anderen Konstruktor delegieren würde. Zum Hinzufügen von delegierenden Konstruktoren verwenden Sie die Syntax `constructor (. . .) : constructor (. . .)`:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

Während Sie das vorherige Beispiel schrittweise ausführen, achten Sie darauf, ob der `class_c(int, int, int)`-Konstruktor zuerst den `class_c(int, int)`-Konstruktor aufruft, der wiederum `class_c(int)` aufruft. Jeder der Konstruktoren führt nur die Aufgaben aus, die nicht von den anderen Konstruktoren ausgeführt werden.

Der erste Konstruktor, der aufgerufen wird, initialisiert das Objekt, sodass alle seine Member zu diesem Zeitpunkt initialisiert werden. Sie können Memberinitialisierungen nicht in einem Konstruktor durchführen, der an einen anderen Konstruktor delegiert wird, wie hier gezeigt:

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

Im folgenden Beispiel wird die Verwendung von nicht statischen Datenmemberinitialisierern verdeutlicht. Wenn ein Konstruktor auch einen angegebenen Datenmember initialisiert, wird der Memberinitialisierer überschrieben:

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

Die Konstruktordelegierungssyntax verhindert nicht die versehentliche Erstellung der Konstruktorrekursion, d. h. Constructor1 ruft Constructor2 auf, der wiederum Constructor1 aufruft. Es wird nur ein Fehler ausgelöst, wenn es zu einem Stapelüberlauf kommt. Sie müssen dafür sorgen, Zyklen zu vermeiden.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
