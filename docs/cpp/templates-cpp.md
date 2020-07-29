---
title: Vorlagen (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 996458417b20533db074ce2fa13c06860c54247c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223563"
---
# <a name="templates-c"></a>Vorlagen (C++)

Vorlagen sind die Grundlage für die generische Programmierung in C++. Als stark typisierte Sprache erfordert C++, dass alle Variablen einen bestimmten Typ aufweisen, der entweder explizit vom Programmierer deklariert oder vom Compiler abgeleitet wurde. Viele Datenstrukturen und Algorithmen sehen jedoch unabhängig von dem Typ, auf dem Sie ausgeführt werden, dieselbe aus. Vorlagen ermöglichen es Ihnen, die Vorgänge einer Klasse oder Funktion zu definieren und den Benutzer anzugeben, an welchen konkreten Typen diese Vorgänge funktionieren sollen.

## <a name="defining-and-using-templates"></a>Definieren und Verwenden von Vorlagen

Eine Vorlage ist ein Konstrukt, das zum Zeitpunkt der Kompilierung einen normalen Typ oder eine gewöhnliche Funktion generiert, basierend auf Argumenten, die der Benutzer für die Vorlagen Parameter bereitstellt. Beispielsweise können Sie eine Funktions Vorlage wie folgt definieren:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Der obige Code beschreibt eine Vorlage für eine generische Funktion mit einem einzelnen Typparameter " *T*", deren Rückgabewert und die aufrufen Parameter (LHS und RHS) alle diesen Typ haben. Sie können einen Typparameter beliebig benennen, aber in der Regel werden einzelne Großbuchstaben in der Konvention verwendet. *T* ist ein Vorlagen Parameter. Das **`typename`** Schlüsselwort gibt an, dass dieser Parameter ein Platzhalter für einen Typ ist. Wenn die-Funktion aufgerufen wird, ersetzt der Compiler jede Instanz von durch `T` das konkrete Typargument, das entweder vom Benutzer angegeben oder vom Compiler abgeleitet wird. Der Prozess, in dem der Compiler eine Klasse oder eine Funktion aus einer Vorlage generiert, wird als *Vorlagen Instanziierung*bezeichnet. `minimum<int>`ist eine Instanziierung der Vorlage `minimum<T>` .

An anderer Stelle kann ein Benutzer eine Instanz der für int spezialisierten Vorlage deklarieren. angenommen, get_a () und get_b () sind Funktionen, die einen int-Wert zurückgeben:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Da es sich hierbei jedoch um eine Funktions Vorlage handelt und der Compiler den Typ von `T` aus den Argumenten *a* und *b*ableiten kann, können Sie ihn genau wie eine gewöhnliche Funktion aufzurufen:

```cpp
int i = minimum(a, b);
```

Wenn der Compiler auf die letzte Anweisung trifft, generiert er eine neue Funktion, in der jedes Vorkommen von *T* in der Vorlage durch Folgendes ersetzt wird **`int`** :

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Die Regeln, wie der Compiler die Typableitung in Funktions Vorlagen ausführt, basieren auf den Regeln für normale Funktionen. Weitere Informationen finden Sie unter [Überladungs Auflösung von Funktions Vorlagen aufrufen](../cpp/overload-resolution-of-function-template-calls.md).

## <a name="type-parameters"></a><a id="type_parameters"></a>Typparameter

`minimum`Beachten Sie in der obigen Vorlage, dass der Typparameter *T* in keiner Weise qualifiziert ist, bis er in den Funktionsaufrufen-Parametern verwendet wird, in denen die Konstanten und Verweis Qualifizierer hinzugefügt werden.

Es gibt keine praktische Beschränkung für die Anzahl der Typparameter. Trennen Sie mehrere Parameter durch Kommas:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

Das-Schlüsselwort **`class`** entspricht **`typename`** in diesem Kontext. Sie können das vorherige Beispiel wie folgt ausdrücken:

```cpp
template <class T, class U, class V> class Foo{};
```

Sie können den Ellipsen Operator (...) verwenden, um eine Vorlage zu definieren, die eine beliebige Anzahl von NULL oder mehr Typparametern annimmt:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Alle integrierten oder benutzerdefinierten Typen können als Typargument verwendet werden. Beispielsweise können Sie [Std:: Vector](../standard-library/vector-class.md) in der-Standard Bibliothek zum Speichern von Variablen des Typs **`int`** , **`double`** , [Std:: String](../standard-library/basic-string-class.md), `MyClass` , **`const`** `MyClass` *, `MyClass&` usw. verwenden. Die primäre Einschränkung bei der Verwendung von Vorlagen besteht darin, dass ein Typargument alle Vorgänge unterstützen muss, die auf die Typparameter angewendet werden. Wenn wir beispielsweise verwenden, `minimum` `MyClass` wie in diesem Beispiel:

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

Ein Compilerfehler wird generiert, da `MyClass` keine Überladung für den Operator bereitstellt **<** .

Es ist nicht zwingend erforderlich, dass die Typargumente für eine bestimmte Vorlage zur gleichen Objekthierarchie gehören. Sie können jedoch auch eine Vorlage definieren, die eine solche Einschränkung erzwingt. Sie können objektorientierte Techniken mit Vorlagen kombinieren. Beispielsweise können Sie ein abgeleitetes * in einem Vektor speichern \<Base\*> .    Beachten Sie, dass die Argumente Zeiger sein müssen.

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Die grundlegenden Anforderungen, die `std::vector` von und anderen Standard Bibliotheks Containern für Elemente von auferlegt `T` werden, sind, dass Sie `T` kopiert und kopiert werden können.

## <a name="non-type-parameters"></a>Nicht-Typparameter

Anders als bei generischen Typen in anderen Sprachen, wie z. b. c# und Java, unterstützen C++-Vorlagen *nicht-Typparameter*, auch als Wert Parameter bezeichnet Beispielsweise können Sie einen Konstanten ganzzahligen Wert bereitstellen, um die Länge eines Arrays anzugeben, wie in diesem Beispiel, das der [Std:: Array](../standard-library/array-class-stl.md) -Klasse in der Standard Bibliothek ähnelt:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Beachten Sie die Syntax in der Vorlagen Deklaration. Der `size_t` Wert wird als Vorlagen Argument zur Kompilierzeit und muss **`const`** oder ein-Ausdruck sein **`constexpr`** . Sie verwenden Sie wie folgt:

```cpp
MyArray<MyClass*, 10> arr;
```

Andere Arten von Werten, einschließlich Zeiger und Verweise, können als nicht-Typparameter angegeben werden. Beispielsweise können Sie einen Zeiger auf ein Funktions-oder Funktions Objekt übergeben, um einen Vorgang innerhalb des Vorlagen Codes anzupassen.

### <a name="type-deduction-for-non-type-template-parameters"></a>Typableitung für Nichttyp-Vorlagen Parameter

In Visual Studio 2017 und höher im Modus **/Std: c++ 17** leitet der Compiler den Typ eines nicht-typvorlagen Arguments ab, das mit deklariert ist **`auto`** :

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Vorlagen als Vorlagen Parameter

Eine Vorlage kann ein Vorlagen Parameter sein. In diesem Beispiel verfügt MyClass2 über zwei Vorlagen Parameter: einen tyname-Parameter *T* und einen Vorlagen Parameter *arr*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Da der *arr* -Parameter selbst keinen Text hat, werden seine Parameternamen nicht benötigt. Tatsächlich ist es ein Fehler, auf die Namen der *arr*-Typnamen oder-Klassen Parameter im Text von zu verweisen `MyClass2` . Aus diesem Grund können die Typparameter Namen von *arr*weggelassen werden, wie im folgenden Beispiel gezeigt:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Standardvorlagen Argumente

Klassen-und Funktions Vorlagen können Standardargumente aufweisen. Wenn eine Vorlage über ein Standardargument verfügt, können Sie Sie nicht angegeben, wenn Sie Sie verwenden. Beispielsweise verfügt die Vorlage "Std:: Vector" über ein Standardargument für die Zuweisung:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

In den meisten Fällen ist die standardmäßige Std:: zuordcator-Klasse akzeptabel, daher verwenden Sie einen Vektor wie den folgenden:

```cpp
vector<int> myInts;
```

Bei Bedarf können Sie jedoch einen benutzerdefinierten Zuweiser wie den folgenden angeben:

```cpp
vector<int, MyAllocator> ints;
```

Bei mehrfachen Vorlagenargumenten müssen alle Argumente nach dem ersten Standardargument Standardargumente haben.

Wenn Sie eine Vorlage verwenden, deren Parameter standardmäßig standardmäßig verwendet werden, verwenden Sie leere eckige Klammern:

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

In einigen Fällen ist es nicht möglich oder wünschenswert, dass eine Vorlage genau denselben Code für einen beliebigen Typ definiert. Beispielsweise möchten Sie möglicherweise einen Codepfad definieren, der nur ausgeführt werden soll, wenn das Typargument ein Zeiger ist, oder eine Std:: wstring-Klasse oder ein von einer bestimmten Basisklasse abgeleiteter Typ.  In solchen Fällen können Sie eine *Spezialisierung* der Vorlage für diesen bestimmten Typ definieren. Wenn ein Benutzer die Vorlage mit diesem Typ instanziiert, verwendet der Compiler die-Spezialisierung, um die-Klasse zu generieren, und für alle anderen Typen wählt der Compiler die allgemeinere Vorlage aus. Spezialisierungen, bei denen alle Parameter spezialisiert sind, sind *vollständige Spezialisierungen*. Wenn nur einige der Parameter spezialisiert sind, wird es als *partielle Spezialisierung*bezeichnet.

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

Eine Vorlage kann beliebig viele Spezialisierungen aufweisen, solange jeder spezialisierte Typparameter eindeutig ist. Nur Klassen Vorlagen können teilweise spezialisiert sein. Alle vollständigen und partiellen Spezialisierungs Arbeiten einer Vorlage müssen im selben Namespace wie die ursprüngliche Vorlage deklariert werden.

Weitere Informationen finden Sie unter [Vorlagen Spezialisierung](../cpp/template-specialization-cpp.md).
