---
title: Konstruktoren (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: b8373eda52967db881d7d58477fcd2a9181ac3ee
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924721"
---
# <a name="constructors-c"></a>Konstruktoren (C++)

Um anzupassen, wie Klassenmember initialisiert werden, oder um Funktionen aufzurufen, wenn ein Objekt der Klasse erstellt wird, definieren Sie einen *Konstruktor* . Ein Konstruktor hat den gleichen Namen wie die Klasse und weist keinen Rückgabewert auf. Sie können beliebig viele überladene Konstruktoren definieren, um die Initialisierung auf verschiedene Weise anzupassen. In der Regel haben Konstruktoren öffentliche Barrierefreiheit, sodass Code außerhalb der Klassendefinition oder Vererbungs Hierarchie Objekte der Klasse erstellen kann. Sie können einen Konstruktor auch als **`protected`** oder deklarieren **`private`** .

Konstruktoren können optional eine Member-init-Liste annehmen. Dies ist eine effizientere Möglichkeit, Klassenmember zu initialisieren, als Werte im Konstruktortext zuzuweisen. Das folgende Beispiel zeigt eine-Klasse `Box` mit drei überladenen Konstruktoren. Die letzten zwei Initialisierungs Listen für Member.

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

Wenn Sie eine Instanz einer Klasse deklarieren, wählt der Compiler basierend auf den Regeln der Überladungs Auflösung aus, welcher Konstruktor aufgerufen werden soll:

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Konstruktoren können als **`inline`** , [explizit](#explicit_constructors) **`friend`** oder [constexpr](#constexpr_constructors)deklariert werden.
- Ein Konstruktor kann ein Objekt initialisieren, das als **`const`** , oder deklariert **`volatile`** wurde **`const volatile`** . Das-Objekt wird **`const`** nach Abschluss des-Konstruktors.
- Um einen Konstruktor in einer Implementierungs Datei zu definieren, benennen Sie ihn wie jede andere Element Funktion mit einem qualifizierten Namen: `Box::Box(){...}` .

## <a name="member-initializer-lists"></a><a name="member_init_list"></a> Member-Initialisiererlisten

Ein Konstruktor kann optional über eine Member-Initialisiererliste verfügen, die Klassenmember vor der Ausführung des konstruktortexts initialisiert. (Beachten Sie, dass eine Member-Initialisiererliste nicht dasselbe ist wie eine *Initialisiererliste* vom Typ [Std \<T> :: initializer_list](../standard-library/initializer-list-class.md).)

Die Verwendung einer Member-Initialisiererliste wird bevorzugt, wenn Werte im Hauptteil des Konstruktors zugewiesen werden, da der Member direkt initialisiert wird. Im folgenden Beispiel wird die Liste der Elementinitialisierer aus allen **bezeichnerausdrücken (Argument)** nach dem Doppelpunkt angezeigt:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Der Bezeichner muss auf einen Klassenmember verweisen. Sie wird mit dem Wert des-Arguments initialisiert. Das Argument kann einer der Konstruktorparameter, ein Funktions-oder ein [Std:: initializer_list \<T> ](../standard-library/initializer-list-class.md)sein.

**`const`** Member und Member des Verweis Typs müssen in der Initialisiererliste des Members initialisiert werden.

Aufrufe der parametrisierten Basisklassenkonstruktoren sollten in der Initialisiererliste vorgenommen werden, um sicherzustellen, dass die Basisklasse vor der Ausführung des abgeleiteten Konstruktors vollständig initialisiert wird.

## <a name="default-constructors"></a><a name="default_constructors"></a> Standardkonstruktoren

*Standardkonstruktoren* verfügen in der Regel über keine Parameter, Sie können jedoch Parameter mit Standardwerten aufweisen.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Standardkonstruktoren sind eine der [speziellen Member-Funktionen](special-member-functions.md). Wenn keine Konstruktoren in einer Klasse deklariert sind, stellt der Compiler einen impliziten **`inline`** Standardkonstruktor bereit.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

Wenn Sie sich auf einen impliziten Standardkonstruktor verlassen, achten Sie darauf, dass Sie Member in der Klassendefinition initialisieren, wie im vorherigen Beispiel gezeigt. Ohne diese Initialisierer würden die Member nicht initialisiert, und der Volume ()-Befehl würde einen Garbage Value verursachen. Im Allgemeinen empfiehlt es sich, Member auf diese Weise zu initialisieren, auch wenn Sie sich nicht auf einen impliziten Standardkonstruktor verlassen.

Sie können verhindern, dass der Compiler einen impliziten Standardkonstruktor erzeugt, indem Sie ihn als [gelöscht](#explicitly_defaulted_and_deleted_constructors)definieren:

```cpp
    // Default constructor
    Box() = delete;
```

Ein vom Compiler generierter Standardkonstruktor wird als gelöscht definiert, wenn Klassenmember nicht standardmäßig konstruiert werden können. Beispielsweise müssen alle Member des-Klassen Typs und ihre Klassentyp Elemente über einen Standardkonstruktor und destrukturtoren verfügen, auf die zugegriffen werden kann. Alle Datenmember des Verweis Typs sowie **`const`** Member müssen über einen Standardmember-Initialisierer verfügen.

Wenn Sie einen vom Compiler generierten Standardkonstruktor aufzurufen und versuchen, Klammern zu verwenden, wird eine Warnung ausgegeben:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Dies ist ein Beispiel für das "Most Vexing Parse"-Problem. Da der Beispielsausdruck entweder als Deklaration einer Funktion oder als Aufruf eines Standardkonstruktors interpretiert werden kann, und da C++-Parser Deklarationen bevorzugen, wird der Ausdruck als Funktionsdeklaration behandelt. Weitere Informationen finden Sie unter [Most vexinganalyse](https://en.wikipedia.org/wiki/Most_vexing_parse).

Wenn nicht standardmäßige Konstruktoren deklariert werden, stellt der Compiler keinen Standardkonstruktor bereit:

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

Wenn eine Klasse keinen Standardkonstruktor hat, kann ein Array von Objekten dieser Klasse nicht allein mithilfe von Syntax in eckigen Klammern erstellt werden. Beispielsweise kann im vorherigen Codeblock ein Array von Feldern nicht folgendermaßen deklariert werden:

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

Sie können jedoch eine Reihe von Initialisiererlisten verwenden, um ein Array von Box-Objekten zu initialisieren:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Weitere Informationen finden Sie unter [Initialisierer](initializers.md).

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a> Kopierkonstruktoren

Ein *Kopierkonstruktor* Initialisiert ein-Objekt, indem die Element Werte aus einem Objekt desselben Typs kopiert werden. Wenn es sich bei den Klassenmembern um einfache Typen handelt, z. b. skalare Werte, genügt der vom Compiler generierte Kopierkonstruktor, und Sie müssen keinen eigenen definieren. Wenn Ihre Klasse eine komplexere Initialisierung erfordert, müssen Sie einen benutzerdefinierten Kopierkonstruktor implementieren. Wenn ein Klassenmember z. b. ein Zeiger ist, müssen Sie einen Kopierkonstruktor definieren, um neuen Speicher zuzuordnen und die Werte aus dem Verweis auf das andere Objekt zu kopieren. Der vom Compiler generierte Kopierkonstruktor kopiert einfach den-Zeiger, sodass der neue Zeiger immer noch auf den Speicherort des anderen zeigt.

Ein Kopierkonstruktor kann eine der folgenden Signaturen aufweisen:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Wenn Sie einen Kopierkonstruktor definieren, sollten Sie auch einen Kopier Zuweisungs Operator (=) definieren. Weitere Informationen finden Sie unter [Zuweisungs](assignment.md) -und [Kopierkonstruktoren und Kopier Zuweisungs Operatoren](copy-constructors-and-copy-assignment-operators-cpp.md).

Sie können verhindern, dass das Objekt kopiert wird, indem Sie den Kopierkonstruktor als gelöscht definieren:

```cpp
    Box (const Box& other) = delete;
```

Der Versuch, das Objekt zu kopieren, erzeugt Fehler *C2280: der Versuch, auf eine gelöschte Funktion zu verweisen* .

## <a name="move-constructors"></a><a name="move_constructors"></a> Bewegungskonstruktoren

Ein *bewegungskonstruktor* ist eine spezielle Member-Funktion, die den Besitz der Daten eines vorhandenen Objekts in eine neue Variable verschiebt, ohne die ursprünglichen Daten zu kopieren. Er nimmt einen rvalue-Verweis als ersten Parameter an, und alle zusätzlichen Parameter müssen über Standardwerte verfügen. Bewegungskonstruktoren können die Effizienz Ihres Programms bei der Übergabe von großen Objekten erheblich steigern.

```cpp
Box(Box&& other);
```

Der Compiler wählt einen bewegungskonstruktor in bestimmten Situationen aus, in denen das Objekt von einem anderen Objekt desselben Typs initialisiert wird, das zerstört wird und seine Ressourcen nicht mehr benötigt. Das folgende Beispiel zeigt einen Fall, wenn ein bewegungskonstruktor durch Überladungs Auflösung ausgewählt wird. Im Konstruktor, der aufruft `get_Box()` , ist der zurückgegebene Wert ein *xValue* (ablaufender Wert). Er ist keiner Variablen zugewiesen und wird daher in den Gültigkeitsbereich übergehen. Um die Motivation für dieses Beispiel zu gewährleisten, geben wir Box einen großen Vektor von Zeichen folgen an, die den Inhalt darstellen. Anstatt den Vektor und seine Zeichen folgen zu kopieren, wird er vom bewegungskonstruktor aus dem ablaufenden Wert "Box" gestiehlt, sodass der Vektor nun zum neuen Objekt gehört. Der-Aufrufvorgang `std::move` ist nur erforderlich, da sowohl `vector` -als auch- `string` Klassen eigene bewegungskonstruktoren implementieren.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Print_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Wenn eine Klasse keinen bewegungskonstruktor definiert, generiert der Compiler einen impliziten, wenn kein Benutzer erklärter Kopierkonstruktor, Kopier Zuweisungs Operator, Verschiebungs Zuweisungs Operator oder Dekonstruktor vorhanden ist. Wenn kein expliziter oder impliziter bewegungskonstruktor definiert ist, verwenden Vorgänge, die andernfalls einen bewegungskonstruktor verwenden, stattdessen den Kopierkonstruktor. Wenn eine Klasse einen bewegungskonstruktor oder Bewegungs Zuweisungs Operator deklariert, wird der implizit deklarierte Kopierkonstruktor als gelöscht definiert.

Ein implizit deklarierter bewegungskonstruktor wird als gelöscht definiert, wenn Member, die Klassentypen sind, einen destrukturtor fehlen oder der Compiler nicht bestimmen kann, welcher Konstruktor für den Verschiebungs Vorgang verwendet werden soll.

Weitere Informationen zum Schreiben eines nicht trivialen bewegungskonstruktors finden Sie unter [bewegungskonstruktoren und Bewegungs Zuweisungs Operatoren (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a> Explizit standardmäßig standardmäßig und gelöschte Konstruktoren

Sie können explizit Kopierkonstruktoren, Standardkonstruktoren, bewegungskonstruktoren, Kopier Zuweisungs Operatoren, Verschiebungs Zuweisungs Operatoren und Dekonstruktoren *standardmäßig* kopieren. Sie können alle speziellen Member-Funktionen explizit *Löschen* .

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

Weitere Informationen finden Sie unter explizit standardmäßig festgelegte [und gelöschte Funktionen](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a> constexpr-Konstruktoren

Ein Konstruktor kann als [constexpr](constexpr-cpp.md) deklariert werden, wenn

- Sie ist entweder als Standard deklariert, oder andernfalls erfüllt Sie alle Bedingungen für [constexpr-Funktionen](constexpr-cpp.md#constexpr_functions) im Allgemeinen.
- die Klasse verfügt über keine virtuellen Basisklassen.
- Jeder Parameter ist ein [Literaltyp](trivial-standard-layout-and-pod-types.md#literal_types).
- der Text ist kein try-Block für eine Funktion.
- alle nicht statischen Datenmember und Basisobjekte der Basisklasse werden initialisiert.
- Wenn die Klasse (a) eine Union mit Variant-Membern ist oder (b) anonyme Unions aufweist, wird nur einer der Union-Member initialisiert.
- alle nicht statischen Datenmember des Klassen Typs und alle Basisklassen-unter Objekte verfügen über einen constexpr-Konstruktor.

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a> Initialisiererlisten-Konstruktoren

Wenn ein Konstruktor einen [Std:: initializer_list \<T\> ](../standard-library/initializer-list-class.md) als Parameter annimmt und alle anderen Parameter Standardargumente aufweisen, wird dieser Konstruktor bei der Überladungs Auflösung ausgewählt, wenn die Klasse durch die direkte Initialisierung instanziiert wird. Sie können den initializer_list verwenden, um alle Member zu initialisieren, die ihn annehmen können. Nehmen Sie beispielsweise an, dass die Box-Klasse (zuvor gezeigt) einen `std::vector<string>` Member hat `m_contents` . Sie können einen Konstruktor wie den folgenden bereitstellen:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Erstellen Sie dann Box-Objekte wie folgt:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a> Explizite Konstruktoren

Wenn eine Klasse einen Konstruktor mit einem einzelnen Parameter aufweist oder wenn alle Parameter mit Ausnahmen von einem einen Standardwert besitzen, kann der Parametertyp impliziert zum Klassentyp konvertiert werden. Beispielsweise wenn die `Box`-Klasse über einen derartigen Konstruktor verfügt:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Es ist möglich, ein Feld wie folgt zu initialisieren:

```cpp
Box b = 42;
```

Alternativ können Sie eine Ganzzahl an eine Funktion weiterleiten, die ein Feld verwendet:

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

Derartige Konvertierungen können in einigen Fällen hilfreich sein. Häufiger führen sie jedoch möglicherweise zu feinen, aber schwerwiegenden Fehlern in Ihrem Code. Als allgemeine Regel sollten Sie das **`explicit`** -Schlüsselwort für einen Konstruktor (und benutzerdefinierte Operatoren) verwenden, um diese Art der impliziten Typkonvertierung zu verhindern:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Wenn der Konstruktor explizit ist, verursacht diese Zeile einen Compilerfehler: `ShippingOrder so(42, 10.8);`.  Weitere Informationen finden Sie unter [benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order-of-construction"></a><a name="order_of_construction"></a> Reihenfolge der Konstruktion

Ein Konstruktor führt die Arbeit in folgender Reihenfolge aus:

1. Er ruft Basisklassen- und Memberkonstruktoren in der Reihenfolge der Deklaration auf.

1. Wenn die Klasse von virtuellen Basisklassen abgeleitet wird, initialisiert er die virtuellen Basiszeiger des Objekts.

1. Wenn die Klasse virtuelle Funktionen hat oder erbt, initialisiert er die virtuellen Funktionszeiger des Objekts. Virtuelle Funktionszeiger zeigen auf die virtuelle Funktionstabelle der Klasse, um eine korrekte Bindung von virtuellen Funktionsaufrufen im Code zu ermöglichen.

1. Er führt den Code im Funktionsrumpf aus.

Das folgende Beispiel zeigt die Reihenfolge, in der Basisklassen- und Memberkonstruktoren im Konstruktor für eine abgeleitete Klasse aufgerufen werden. Zuerst wird der Basiskonstruktor aufgerufen. Anschließend werden die Basisklassenmember in der Reihenfolge initialisiert, in der sie in der Klassendeklaration stehen. Danach wird der abgeleitete Konstruktor aufgerufen.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

So sieht die Ausgabe aus:

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Ein abgeleiteter Klassenkonstruktor ruft immer einen Basisklassenkonstruktor auf, damit er immer auf vollständig erstellte Basisklassen zurückgreifen kann, bevor zusätzliche Arbeit erforderlich ist. Die Basisklassenkonstruktoren werden in der Reihenfolge der Ableitung aufgerufen, z. – `ClassA` . wenn von abgeleitet ist `ClassB` , das von abgeleitet wird `ClassC` , der `ClassC` Konstruktor zuerst aufgerufen wird, dann der `ClassB` Konstruktor und dann der `ClassA` Konstruktor.

Wenn eine Basisklasse keinen Standardkonstruktor hat, müssen Sie die Parameter für den Basisklassenkonstruktor im abgeleiteten Klassenkonstruktor angeben:

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

Wenn ein Konstruktor eine Ausnahme auslöst, ist die Reihenfolge der Zerstörung die umgekehrte Reihenfolge der Erstellung:

1. Der Code im Text der Konstruktorfunktion wird entladen.

1. Basisklassen- und Memberobjekte werden in der umgekehrten Reihenfolge der Deklaration zerstört.

1. Wenn der Konstruktor nicht delegierend ist, werden alle vollständig erstellten Basisklassenobjekte und Member zerstört. Da jedoch das Objekt selbst nicht vollständig erstellt wird, wird der Destruktor nicht ausgeführt.

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a> Abgeleitete Konstruktoren und erweiterte Aggregat Initialisierung

Wenn der Konstruktor einer Basisklasse nicht öffentlich ist, aber für eine abgeleitete Klasse zugänglich ist, können Sie im **/Std: c++ 17** -Modus in Visual Studio 2017 und höher keine leeren geschweiften Klammern verwenden, um ein Objekt des abgeleiteten Typs zu initialisieren.

Im folgenden Beispiel ist das konforme Verhalten von C++14 dargestellt:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

In C++17 gilt `Derived` nun als Aggregattyp. Das bedeutet, dass die Initialisierung von `Base` über den privaten Standardkonstruktor direkt als Teil der erweiterten Aggregatinitialisierungsregel erfolgt. Zuvor wurde der private Konstruktor `Base` über den `Derived`-Konstruktor aufgrund der Friend-Deklaration erfolgreich aufgerufen.

Das folgende Beispiel zeigt das Verhalten von c++ 17 in Visual Studio 2017 und höher im **/Std: c++ 17** -Modus:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktoren für Klassen mit Mehrfachvererbung

Wenn eine Klasse von mehreren Basisklassen abgeleitet ist, werden die Basisklassenkonstruktoren in der Reihenfolge aufgerufen, in der sie in der Deklaration der abgeleiteten Klasse aufgelistet sind:

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

Die folgende Ausgabe sollte angezeigt werden:

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a> Delegieren von Konstruktoren

Ein *delegierenden Konstruktor* Ruft einen anderen Konstruktor in derselben Klasse auf, um einen Teil der Initialisierung zu durchführen. Dies ist nützlich, wenn Sie über mehrere Konstruktoren verfügen, die alle ähnliche Aufgaben ausführen müssen. Sie können die Hauptlogik in einem Konstruktor schreiben und von anderen aufrufen. Im folgenden trivialen Beispiel delegiert Box (int) seine Arbeit an Box (int, int, int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

Das von den Konstruktoren erstellte Objekt wird vollständig initialisiert, sobald jeder Konstruktor abgeschlossen ist. Weitere Informationen finden Sie unter [Delegieren von Konstruktoren](../cpp/delegating-constructors.md).

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a> Erbende Konstruktoren (c++ 11)

Eine abgeleitete Klasse kann die Konstruktoren von einer direkten Basisklasse erben, indem eine Deklaration verwendet wird, **`using`** wie im folgenden Beispiel gezeigt:

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=msvc-150"

**Visual Studio 2017 und** höher: **`using`** bei der Anweisung im **/Std: c++ 17** -Modus werden alle Konstruktoren der Basisklasse mit Ausnahme derjenigen, die in der abgeleiteten Klasse eine identische Signatur aufweisen, in den Gültigkeitsbereich integriert. Im Allgemeinen empfiehlt es sich, erbende Konstruktoren zu verwenden, wenn die abgeleitete Klasse keine neuen Datenmember oder Konstruktoren deklariert.

::: moniker-end

Eine Klassenvorlage kann alle Konstruktoren aus einem Typargument erben, wenn dieser Typ eine Basisklasse angibt:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Eine erbende Klasse kann nicht aus mehreren Basisklassen erben, wenn diese Basisklassen über Konstruktoren mit einer identischen Signatur verfügen.

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a> Konstruktoren und zusammengesetzte Klassen

Klassen, die Klassentyp Member enthalten, werden als zusammen *gesetzte Klassen* bezeichnet. Wenn ein Klassentypmember einer zusammengesetzten Klasse erstellt wird, wird der Konstruktor vor dem Konstruktor der Klasse aufgerufen. Wenn einer enthaltenen Klasse ein Standardkonstruktor fehlt, müssen Sie eine Initialisierungsliste im Konstruktor der zusammengesetzten Klasse verwenden. Wenn Sie im `StorageBox`-Beispiel oben den Typ der `m_label`-Membervariable in eine neue `Label`-Klasse ändern, müssen Sie den Basisklassenkonstruktor aufrufen und die `m_label`-Variable im `StorageBox`-Konstruktor initialisieren:

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>In diesem Abschnitt

- [Kopierkonstruktoren und Kopierzuweisungsoperatoren](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Bewegungskonstruktoren und Bewegungszuweisungsoperatoren](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegierende Konstruktoren](delegating-constructors.md)

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](classes-and-structs-cpp.md)
