---
title: union
description: Eine Beschreibung des Standard mäßigen C++ union class -Typs und-Schlüssel Worts, dessen Verwendung und Einschränkungen.
ms.date: 08/18/2020
f1_keywords:
- union_cpp
helpviewer_keywords:
- class type [C++], union as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
no-loc:
- union
- struct
- enum
- class
- static
ms.openlocfilehash: a4dc07df5e7858dffe62478509ee1d8dc759ce96
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88722179"
---
# `union`

> [!NOTE]
> In c++ 17 und höher `std::variant` class ist eine typsichere Alternative für eine union .

Ein **`union`** ist ein benutzerdefinierter Typ, in dem alle Member denselben Speicherort verwenden. Diese Definition bedeutet, dass ein-Objekt zu jedem beliebigen Zeitpunkt nur ein union Objekt aus der Liste der Elemente enthalten kann. Dies bedeutet auch, dass unabhängig davon, wie viele Member a vorhanden ist union , immer nur ausreichend Arbeitsspeicher verwendet wird, um das größte Element zu speichern.

Ein union kann nützlich sein, um Speicherplatz zu sparen, wenn Sie über viele Objekte und begrenzten Arbeitsspeicher verfügen. Eine erfordert jedoch union besondere Sorgfalt, um richtig zu verwenden. Sie sind dafür verantwortlich, sicherzustellen, dass Sie immer auf denselben Member zugreifen, den Sie zugewiesen haben. Wenn Elementtypen über ein nicht triviales con struct oder verfügen, müssen Sie zusätzlichen Code schreiben, um diesen Member explizit zu erstellen struct und zu zerstören. Bevor Sie eine verwenden union , sollten Sie überprüfen, ob das Problem, das Sie lösen möchten, mithilfe eines Basis class -und abgeleiteten Typs besser ausgedrückt werden kann class .

## <a name="syntax"></a>Syntax

> **`union`***`tag`* <sub>opt</sub> **`{`** opt *`member-list`***`};`**

### <a name="parameters"></a>Parameter

*`tag`*<br/>
Der Typname, der an den übergeben wird union .

*`member-list`*<br/>
Member, die der union enthalten kann.

## <a name="declare-a-no-locunion"></a>Deklarieren union

Beginnen Sie mit dem-Schlüsselwort mit der Deklaration von union **`union`** , und schließen Sie die Elementliste in geschweiften Klammern ein:

```cpp
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};

int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```

## <a name="use-a-no-locunion"></a>Verwenden Sie eine union

Im vorherigen Beispiel muss jeder Code, der auf das zugreift, union wissen, welcher Member die Daten enthält. Die gängigste Lösung für dieses Problem wird als * union *Unterscheidungs bezeichnet. Sie schließt union in ein ein struct und schließt einen Member ein, enum der den derzeit im gespeicherten Elementtyp angibt union . Das grundlegende Muster wird im folgenden Beispiel veranschaulicht:

```cpp
#include <queue>

using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    int StationId;
    time_t time;
    double current;
    double max;
    double min;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    WeatherDataType type;
    union
    {
        TempData temp;
        WindData wind;
    };
};

// Functions that are specific to data types
void Process_Temp(TempData t) {}
void Process_Wind(WindData w) {}

void Initialize(std::queue<Input>& inputs)
{
    Input first;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    Input second;
    second.type = WeatherDataType::Wind;
    second.wind = { 204, 1418859354, 14, 27 };
    inputs.push(second);
}

int main(int argc, char* argv[])
{
    // Container for all the data records
    queue<Input> inputs;
    Initialize(inputs);
    while (!inputs.empty())
    {
        Input const i = inputs.front();
        switch (i.type)
        {
        case WeatherDataType::Temperature:
            Process_Temp(i.temp);
            break;
        case WeatherDataType::Wind:
            Process_Wind(i.wind);
            break;
        default:
            break;
        }
        inputs.pop();

    }
    return 0;
}
```

Im vorherigen Beispiel union hat der in der `Input` struct keinen Namen, daher wird er als *Anonym* bezeichnet union . Auf seine Member kann direkt zugegriffen werden, als ob Sie Elemente von sind struct . Weitere Informationen zur Verwendung eines anonymen finden Sie union im Abschnitt " [ union Anonym](#anonymous_unions) ".

Das vorherige Beispiel zeigt ein Problem, das Sie auch durch die Verwendung von Typen lösen können class , die von einer gemeinsamen Basis abgeleitet werden class . Sie könnten den Code auf Grundlage des Lauf Zeit Typs jedes Objekts im Container verzweigen. Der Code ist möglicherweise einfacher zu verwalten und zu verstehen, kann aber auch langsamer als die Verwendung eines sein union . Mit einem können Sie auch nicht verknüpfte union Typen speichern. unionMit einem können Sie den Typ des gespeicherten Werts dynamisch ändern, ohne den Typ der union Variablen selbst zu ändern. Beispielsweise können Sie ein heterogenes Array von erstellen `MyUnionType` , dessen Elemente verschiedene Werte verschiedener Typen speichern.

Es ist einfach, die `Input` struct im Beispiel zu missbrauchen. Der Benutzer muss den Diskriminator ordnungsgemäß verwenden, um auf den Member zuzugreifen, der die Daten enthält. Sie können vor Missbrauch schützen, indem Sie den union **`private`** und spezielle Zugriffs Funktionen bereitstellen, wie im folgenden Beispiel gezeigt.

## <a name="unrestricted-no-locunion-c11"></a>Uneingeschränkt union (c++ 11)

In c++ 03 und früheren Versionen union kann ein nicht- static Datenmember mit einem-Typ enthalten, solange der- class Typ keine von Benutzern bereitgestellten con struct ORS, de struct ORS oder Zuweisungs Operatoren hat. In C++11 wurden diese Einschränkungen entfernt. Wenn Sie einen solchen Member in ihren einschließen union , markiert der Compiler automatisch alle speziellen Member-Funktionen, die nicht als Benutzer bereitgestellt werden **`deleted`** . Wenn union ein anonymer innerhalb eines-oder-Elements ist union class struct , werden alle speziellen Member-Funktionen von class oder struct , die nicht vom Benutzer bereitgestellt werden, als markiert **`deleted`** . Im folgenden Beispiel wird gezeigt, wie Sie diesen Fall behandeln können. Einer der union Member der verfügt über einen Member, der diese besondere Behandlung erfordert:

```cpp
// for MyVariant
#include <crtdbg.h>
#include <new>
#include <utility>

// for sample objects and output
#include <string>
#include <vector>
#include <iostream>

using namespace std;

struct A
{
    A() = default;
    A(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    //...
};

struct B
{
    B() = default;
    B(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    vector<int> vec;
    // ...
};

enum class Kind { None, A, B, Integer };

#pragma warning (push)
#pragma warning(disable:4624)
class MyVariant
{
public:
    MyVariant()
        : kind_(Kind::None)
    {
    }

    MyVariant(Kind kind)
        : kind_(kind)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A();
            break;
        case Kind::B:
            new (&b_) B();
            break;
        case Kind::Integer:
            i_ = 0;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    ~MyVariant()
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            a_.~A();
            break;
        case Kind::B:
            b_.~B();
            break;
        case Kind::Integer:
            break;
        default:
            _ASSERT(false);
            break;
        }
        kind_ = Kind::None;
    }

    MyVariant(const MyVariant& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(other.a_);
            break;
        case Kind::B:
            new (&b_) B(other.b_);
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    MyVariant(MyVariant&& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(move(other.a_));
            break;
        case Kind::B:
            new (&b_) B(move(other.b_));
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
    }

    MyVariant& operator=(const MyVariant& other)
    {
        if (&other != this)
        {
            switch (other.kind_)
            {
            case Kind::None:
                this->~MyVariant();
                break;
            case Kind::A:
                *this = other.a_;
                break;
            case Kind::B:
                *this = other.b_;
                break;
            case Kind::Integer:
                *this = other.i_;
                break;
            default:
                _ASSERT(false);
                break;
            }
        }
        return *this;
    }

    MyVariant& operator=(MyVariant&& other)
    {
        _ASSERT(this != &other);
        switch (other.kind_)
        {
        case Kind::None:
            this->~MyVariant();
            break;
        case Kind::A:
            *this = move(other.a_);
            break;
        case Kind::B:
            *this = move(other.b_);
            break;
        case Kind::Integer:
            *this = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
        return *this;
    }

    MyVariant(const A& a)
        : kind_(Kind::A), a_(a)
    {
    }

    MyVariant(A&& a)
        : kind_(Kind::A), a_(move(a))
    {
    }

    MyVariant& operator=(const A& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(a);
        }
        else
        {
            a_ = a;
        }
        return *this;
    }

    MyVariant& operator=(A&& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(move(a));
        }
        else
        {
            a_ = move(a);
        }
        return *this;
    }

    MyVariant(const B& b)
        : kind_(Kind::B), b_(b)
    {
    }

    MyVariant(B&& b)
        : kind_(Kind::B), b_(move(b))
    {
    }

    MyVariant& operator=(const B& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(b);
        }
        else
        {
            b_ = b;
        }
        return *this;
    }

    MyVariant& operator=(B&& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(move(b));
        }
        else
        {
            b_ = move(b);
        }
        return *this;
    }

    MyVariant(int i)
        : kind_(Kind::Integer), i_(i)
    {
    }

    MyVariant& operator=(int i)
    {
        if (kind_ != Kind::Integer)
        {
            this->~MyVariant();
            new (this) MyVariant(i);
        }
        else
        {
            i_ = i;
        }
        return *this;
    }

    Kind GetKind() const
    {
        return kind_;
    }

    A& GetA()
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    const A& GetA() const
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    B& GetB()
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    const B& GetB() const
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    int& GetInteger()
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

    const int& GetInteger() const
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

private:
    Kind kind_;
    union
    {
        A a_;
        B b_;
        int i_;
    };
};
#pragma warning (pop)

int main()
{
    A a(1, "Hello from A");
    B b(2, "Hello from B");

    MyVariant mv_1 = a;

    cout << "mv_1 = a: " << mv_1.GetA().name << endl;
    mv_1 = b;
    cout << "mv_1 = b: " << mv_1.GetB().name << endl;
    mv_1 = A(3, "hello again from A");
    cout << R"aaa(mv_1 = A(3, "hello again from A"): )aaa" << mv_1.GetA().name << endl;
    mv_1 = 42;
    cout << "mv_1 = 42: " << mv_1.GetInteger() << endl;

    b.vec = { 10,20,30,40,50 };

    mv_1 = move(b);
    cout << "After move, mv_1 = b: vec.size = " << mv_1.GetB().vec.size() << endl;

    cout << endl << "Press a letter" << endl;
    char c;
    cin >> c;
}
```

Ein union kann keinen Verweis speichern. Ein union unterstützt auch keine Vererbung. Dies bedeutet, dass Sie keine union als Basis verwenden class oder von einem anderen erben können class oder über virtuelle Funktionen verfügen.

## <a name="initialize-a-no-locunion"></a>Initialisieren eines union

Sie können eine in derselben Anweisung deklarieren und initialisieren, union indem Sie einen Ausdruck zuweisen, der in geschweiften Klammern eingeschlossen ist. Der Ausdruck wird ausgewertet und dem ersten Feld des zugewiesen union .

```cpp
#include <iostream>
using namespace std;

union NumericType
{
    short       iValue;
    long        lValue;
    double      dValue;
};

int main()
{
    union NumericType Values = { 10 };   // iValue = 10
    cout << Values.iValue << endl;
    Values.dValue = 3.1416;
    cout << Values.dValue << endl;
}
/* Output:
10
3.141600
*/
```

Die `NumericType` union wird wie in der folgenden Abbildung dargestellt im Arbeitsspeicher angeordnet (konzeptionell).

![Speicherung von Daten in einem numerischen Typ::: NO-LOC (Union):::](../cpp/media/vc38ul1.png "Speicherung von Daten in einem numerictype::: NO-LOC (Union):::") <br/>
Speicherung von Daten in einem `NumericType`union

## <a name="anonymous-no-locunion"></a><a name="anonymous_unions"></a> Anonymous union

Eine anonyme union ist eine, die ohne *`class-name`* oder deklariert ist *`declarator-list`* .

> **`union  {`**  *`member-list`*  **`}`**

Namen, die in einem anonymen deklariert union sind, werden direkt verwendet, wie nicht-Member-Variablen. Dies impliziert, dass die in einem anonymen deklarierten Namen union im umgebenden Bereich eindeutig sein müssen.

Ein anonymer union unterliegt diesen zusätzlichen Einschränkungen:

- Wenn Sie im Datei-oder Namespace-Gültigkeitsbereich deklariert ist, muss Sie auch als deklariert werden **`static`** .

- Sie kann nur über Member verfügen; die Verwendung von **`public`** **`private`** -und-Membern **`protected`** in einem anonymen union generiert Fehler.

- Es können keine Element Funktionen vorhanden sein.

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`class`](../cpp/class-cpp.md)<br/>
[`struct`](../cpp/struct-cpp.md)
