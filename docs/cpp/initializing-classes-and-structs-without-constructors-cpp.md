---
title: Brace-Initialisierung für Klassen, Strukturen und Unions
description: Verwenden der Geschweifkontoinitialisierung mit jeder C++-Klasse, -Struktur oder -Union
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374075"
---
# <a name="brace-initialization"></a>Initialisierung mit geschweiften Klammern

Es ist nicht immer erforderlich, einen Konstruktor für eine Klasse zu definieren, insbesondere bei einfachen. Benutzer können Objekte einer Klasse oder Struktur mithilfe einer einheitlichen Initialisierung initialisieren, wie dies aus dem folgenden Beispiel hervorgeht:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Beachten Sie, dass Sie die Listenelemente in der Reihenfolge bereitstellen, in der die Member in der Klasse deklariert werden, wenn eine Klasse oder Struktur keinen Konstruktor hat. Wenn die Klasse über einen Konstruktor verfügt, geben Sie die Elemente in der Reihenfolge der Parameter an. Wenn ein Typ einen Standardkonstruktor hat, der entweder implizit oder explizit deklariert wurde, können Sie die Standardinitialisierung mit geschweiften klammern verwenden (mit leeren Klammern). Beispielsweise kann die folgende Klasse durch Verwenden der standardmäßigen und nicht standardmäßigen Initialisierung mit geschweiften Klammern initialisiert werden:

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

Wenn eine Klasse nicht standardmäßige Konstruktoren enthält, ist die Reihenfolge, in der Klassenmember im Initialisierer für geschweifte Klammern angezeigt werden, die Reihenfolge, in der die entsprechenden Parameter im Konstruktor angezeigt werden, und nicht die Reihenfolge, in der die Member deklariert werden (wie für `class_a` im vorherigen Beispiel). Wenn der Typ andernfalls keinen deklarierten Konstruktor hat, ist die Reihenfolge, in der die Member im Initialisierer für geschweifte Klammern angezeigt werden, dieselbe Reihenfolge, in der sie deklariert werden. In diesem Fall können Sie beliebig viele öffentliche Member initialisieren, Sie dürfen jedoch keinen Member überspringen. Das folgende Beispiel zeigt die Reihenfolge, die für die Initialisierung mit geschweiften Klammern verwendet wird, wenn kein deklarierter Konstruktor vorhanden ist:

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

Wenn der Standardkonstruktor explizit deklariert wird, jedoch als gelöscht markiert wurde, kann die Standardinitialisierung mit geschweiften Klammern nicht angewendet werden:

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

Sie können die Geschweiseninitialisierung überall dort verwenden, wo Sie normalerweise initialisieren würden, z. B. als Funktionsparameter oder Rückgabewert oder mit dem **neuen** Schlüsselwort:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

Im **Modus /std:c++17** sind die Regeln für die leere Initialisierung von Klammern etwas restriktiver. Siehe [Abgeleitete Konstruktoren und erweiterte Aggregatinitialisierung](constructors-cpp.md#extended_aggregate).

## <a name="initializer_list-constructors"></a>initializer_list Konstruktoren

Die [initializer_list-Klasse](../standard-library/initializer-list-class.md) stellt eine Liste von Objekten eines angegebenen Typs dar, die in einem Konstruktor und in anderen Kontexten verwendet werden können. Sie können ein initializer_list-Objekt durch Verwenden der Initialisierung mit geschweiften Klammern erstellen:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> Um diese Klasse verwenden zu [ \<](../standard-library/initializer-list.md) können, müssen Sie den initializer_list>-Header einschließen.

Ein `initializer_list`-Objekt kann kopiert werden. In diesem Fall sind die Member der neuen Liste Verweise auf die Member der ursprünglichen Liste:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Die Standard-Bibliothekscontainerklassen sowie `string`, `wstring` und `regex` verfügen über `initializer_list`-Konstruktoren. Die folgenden Beispiele zeigen, wie die Initialisierung mit geschweiften Klammern mit diesen Konstruktoren durchgeführt wird:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktoren](../cpp/constructors-cpp.md)
