---
title: Vorlagen (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032342"
---
# <a name="templates-c"></a>Vorlagen (C++)

Vorlagen sind die Grundlage für die allgemeine Programmierung in C++. Als stark typisierte Sprache erfordert C++, dass alle Variablen einen bestimmten Typ haben, entweder explizit vom Programmierer deklariert oder vom Compiler abgeleitet werden. Viele Datenstrukturen und Algorithmen sehen jedoch gleich aus, unabhängig davon, auf welchem Typ sie arbeiten. Mithilfe von Vorlagen können Sie die Vorgänge einer Klasse oder Funktion definieren und dem Benutzer die konkreten Typen angeben, an denen diese Vorgänge ausgeführt werden sollen.

## <a name="defining-and-using-templates"></a>Definieren und Verwenden von Vorlagen

Eine Vorlage ist ein Konstrukt, das einen normalen Typ oder eine normale Funktion zur Kompilierungszeit generiert, basierend auf Argumenten, die der Benutzer für die Vorlagenparameter bereitstellt. Sie können z. B. eine Funktionsvorlage wie folgt definieren:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Der obige Code beschreibt eine Vorlage für eine generische Funktion mit einem einzelnen Typparameter *T*, dessen Rückgabewert und Aufrufparameter (lhs und rhs) alle von diesem Typ sind. Sie können einen Typparameter ganz nach Bewilliken benennen, aber konventionell werden am häufigsten einzelne Großbuchstaben verwendet. *T* ist ein Vorlagenparameter; Das **Typename-Schlüsselwort** besagt, dass dieser Parameter ein Platzhalter für einen Typ ist. Wenn die Funktion aufgerufen wird, ersetzt `T` der Compiler jede Instanz von durch das Argument des konkreten Typs, das entweder vom Benutzer angegeben oder vom Compiler abgeleitet wird. Der Prozess, bei dem der Compiler eine Klasse oder Funktion aus einer Vorlage generiert, wird als *Vorlageninstanziierung*bezeichnet. `minimum<int>` ist eine Instanziierung `minimum<T>`der Vorlage .

An anderer Stelle kann ein Benutzer eine Instanz der Vorlage deklarieren, die für int spezialisiert ist. Angenommen, get_a() und get_b() sind Funktionen, die eine int zurückgeben:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Da es sich jedoch um eine Funktionsvorlage handelt und `T` der Compiler den Typ der Argumente *a* und *b*ableiten kann, können Sie sie wie eine gewöhnliche Funktion aufrufen:

```cpp
int i = minimum(a, b);
```

Wenn der Compiler auf diese letzte Anweisung trifft, generiert er eine neue Funktion, in der jedes Vorkommen von *T* in der Vorlage durch **int**ersetzt wird:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Die Regeln für die Art und Weise, wie der Compiler den Typabzug in Funktionsvorlagen ausführt, basieren auf den Regeln für normale Funktionen. Weitere Informationen finden Sie unter [Überladen der Auflösung von Funktionsvorlagenaufrufen](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Typparameter

Beachten `minimum` Sie in der obigen Vorlage, dass der Typparameter *T* in keiner Weise qualifiziert ist, bis er in den Funktionsaufrufparametern verwendet wird, wo die const- und Reference-Qualifizierer hinzugefügt werden.

Es gibt keine praktische Begrenzung für die Anzahl der Typparameter. Trennen Sie mehrere Parameter durch Kommas:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

Die **Schlüsselwortklasse** entspricht in diesem Kontext **dem Typnamen.** Sie können das vorherige Beispiel wie:

```cpp
template <class T, class U, class V> class Foo{};
```

Sie können den Auslassungsoperator (...) verwenden, um eine Vorlage zu definieren, die eine beliebige Anzahl von Null- oder mehr Typparametern verwendet:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Jeder integrierte oder benutzerdefinierte Typ kann als Typargument verwendet werden. Sie können z. B. [std::vector](../standard-library/vector-class.md) in der Standardbibliothek verwenden, um Variablen vom `MyClass`Typ **int**, **double**, [std::string](../standard-library/basic-string-class.md), **, const** `MyClass`*, `MyClass&`, usw. zu speichern. Die primäre Einschränkung bei der Verwendung von Vorlagen besteht darin, dass ein Typargument alle Vorgänge unterstützen muss, die auf die Typparameter angewendet werden. Wenn wir z. `minimum` `MyClass` B. die Verwendung wie in diesem Beispiel aufrufen:

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

Ein Compilerfehler wird `MyClass` generiert, da er keine **<** Überladung für den Operator bietet.

Es ist nicht erforderlich, dass die Typargumente für eine bestimmte Vorlage alle zur gleichen Objekthierarchie gehören, obwohl Sie eine Vorlage definieren können, die eine solche Einschränkung erzwingt. Sie können objektorientierte Techniken mit Vorlagen kombinieren. Sie können z. B. einen\<Abgeleiteten* in einem Vektor Basis->\* speichern.    Beachten Sie, dass die Argumente Zeiger sein müssen

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Die grundlegenden `std::vector` Anforderungen, die und andere `T` Standardbibliothekscontainer an Elemente von stellen, sind, dass `T` sie kopierfähig und kopierfähig sind.

## <a name="non-type-parameters"></a>Nicht-Typ-Parameter

Im Gegensatz zu generischen Typen in anderen Sprachen, wie z. B. C- und Java, unterstützen *C++-Vorlagen Nicht-Typparameter*, die auch als Wertparameter bezeichnet werden. Sie können z. B. einen konstanten integralen Wert angeben, um die Länge eines Arrays anzugeben, wie in diesem Beispiel, das der [std::array-Klasse](../standard-library/array-class-stl.md) in der Standardbibliothek ähnelt:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Beachten Sie die Syntax in der Vorlagendeklaration. Der `size_t` Wert wird zur Kompilierungszeit als Vorlagenargument übergeben und muss **const** oder ein **constexpr-Ausdruck** sein. Sie verwenden es wie folgt:

```cpp
MyArray<MyClass*, 10> arr;
```

Andere Arten von Werten, einschließlich Zeiger und Verweise, können als Nicht-Typparameter übergeben werden. Sie können z. B. einen Zeiger an ein Funktions- oder Funktionsobjekt übergeben, um einen Vorgang innerhalb des Vorlagencodes anzupassen.

### <a name="type-deduction-for-non-type-template-parameters"></a>Typabzug für Nicht-Typ-Vorlagenparameter

In Visual Studio 2017 und höher leitet der Compiler im **/std:c++17-Modus** den Typ eines Nicht-Typvorlagenarguments ab, das mit **auto**deklariert wird:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Vorlagen als Vorlagenparameter

Eine Vorlage kann ein Vorlagenparameter sein. In diesem Beispiel verfügt MyClass2 über zwei Vorlagenparameter: einen Typnamenparameter *T* und einen Vorlagenparameter *Arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Da der *Parameter Arr* selbst keinen Text hat, werden seine Parameternamen nicht benötigt. Tatsächlich ist es ein Fehler, auf den Typnamen oder die Klassenparameternamen von *Arr*innerhalb des Textes von `MyClass2`zu verweisen. Aus diesem Grund können die Parameternamen des *Typs Von Arr*weggelassen werden, wie in diesem Beispiel gezeigt:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Standardvorlagenargumente

Klassen- und Funktionsvorlagen können Standardargumente haben. Wenn eine Vorlage über ein Standardargument verfügt, können Sie es bei der Verwendung nicht angegeben. Die Std::vector-Vorlage verfügt beispielsweise über ein Standardargument für den Zuweisungsfaktor:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

In den meisten Fällen ist die standardmäßige std::allocator-Klasse akzeptabel, daher verwenden Sie einen Vektor wie folgt:

```cpp
vector<int> myInts;
```

Bei Bedarf können Sie jedoch einen benutzerdefinierten Allokator wie folgt angeben:

```cpp
vector<int, MyAllocator> ints;
```

Bei mehrfachen Vorlagenargumenten müssen alle Argumente nach dem ersten Standardargument Standardargumente haben.

Wenn Sie eine Vorlage verwenden, deren Parameter alle standardmäßig sind, verwenden Sie leere winkele Klammern:

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>Vorlagenspezialisierung

In einigen Fällen ist es nicht möglich oder wünschenswert, dass eine Vorlage genau denselben Code für einen beliebigen Typ definiert. Sie können z. B. einen Codepfad definieren, der nur ausgeführt werden soll, wenn es sich bei dem Typargument um einen Zeiger oder um einen std::wstring oder einen Von einer bestimmten Basisklasse abgeleiteten Typ handelt.  In solchen Fällen können Sie eine *Spezialisierung* der Vorlage für diesen bestimmten Typ definieren. Wenn ein Benutzer die Vorlage mit diesem Typ instanziiert, verwendet der Compiler die Spezialisierung, um die Klasse zu generieren, und für alle anderen Typen wählt der Compiler die allgemeinere Vorlage aus. Spezialisierungen, auf die sich alle Parameter spezialisiert haben, sind *komplette Spezialisierungen.* Wenn nur einige der Parameter spezialisiert sind, wird es als *Partielle Spezialisierung*bezeichnet.

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

Eine Vorlage kann eine beliebige Anzahl von Spezialisierungen aufweisen, solange jeder spezielle Typparameter eindeutig ist. Nur Klassenvorlagen können teilweise spezialisiert sein. Alle vollständigen und teilweisen Spezialisierungen einer Vorlage müssen im gleichen Namespace wie die ursprüngliche Vorlage deklariert werden.

Weitere Informationen finden Sie unter [Vorlagenspezialisierung](../cpp/template-specialization-cpp.md).
