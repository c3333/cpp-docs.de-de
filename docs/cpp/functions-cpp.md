---
title: Funktionen (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- defaults, arguments
- function definitions
- function definitions, about function definitions
- default arguments
- declarators, functions
ms.assetid: 33ba01d5-75b5-48d2-8eab-5483ac7d2274
ms.openlocfilehash: 5beadbbf283a64f12dab7f0ee39a267ec1797861
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213436"
---
# <a name="functions-c"></a>Funktionen (C++)

Eine Funktion ist ein Codeblock, der einige Vorgänge ausführt. Eine Funktion kann optional Eingabeparameter definieren, die Aufrufern ermöglichen, Argumente in die Funktion weiterzugeben. Eine Funktion kann einen Wert optional als Ausgabe zurückgeben. Funktionen sind für das Kapseln allgemeiner Vorgänge in einem einzelnen wiederverwendbaren Block nützlich, und zwar ideal unter Verwendung eines Namens, der deutlich das beschreibt, was die Funktion vornimmt. Die folgende Funktion akzeptiert zwei ganze Zahlen von einem Aufrufer und gibt Ihre Summe zurück. *a* und *b* sind *Parameter* vom Typ **`int`** .

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Die Funktion kann von einer beliebigen Anzahl von Stellen im Programm aufgerufen oder *aufgerufen*werden. Die an die Funktion übergebenen Werte sind die *Argumente*, deren Typen mit den Parametertypen in der Funktionsdefinition kompatibel sein müssen.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Es gibt keine praktische Begrenzung für die Funktionslänge, jedoch angemessene Entwurfsziele für Funktionen, die eine einzelne klar definierte Aufgabe ausführen. Komplexe Algorithmen sollten möglichst in leicht verständliche einfachere Funktionen aufgeschlüsselt werden.

Im Klassenbereich definierte Funktionen werden als Memberfunktionen bezeichnet. In C++ kann eine Funktion im Gegensatz zu anderen Sprachen auch im Namespacebereich (einschließlich des impliziten globalen Namespace) definiert werden. Solche Funktionen werden als *Kostenlose Funktionen* oder als *nicht-Member-Funktionen*bezeichnet. Sie werden in der Standard Bibliothek ausführlich verwendet.

Funktionen können *überladen*werden. Dies bedeutet, dass unterschiedliche Versionen einer Funktion denselben Namen haben können, wenn Sie sich durch die Anzahl und/oder den Typ formaler Parameter unterscheiden. Weitere Informationen finden Sie unter [Funktions Überladung](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Bestandteile einer Funktionsdeklaration

Eine minimale Funktions *Deklaration* besteht aus dem Rückgabetyp, dem Funktionsnamen und der Parameterliste (die leer sein kann) sowie optionalen Schlüsselwörtern, die dem Compiler zusätzliche Anweisungen bereitstellen. Das folgende Beispiel ist eine Funktionsdeklaration:

```cpp
int sum(int a, int b);
```

Eine Funktionsdefinition besteht aus einer Deklaration und dem *Text*, der den gesamten Code zwischen den geschweiften Klammern umfasst:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Eine Funktionsdeklaration, auf die ein Semikolon folgt, wird möglicherweise an mehreren Stellen in einem Programm angezeigt. Sie muss vor dem Aufrufen dieser Funktion in jeder Übersetzungseinheit angezeigt werden. Die Funktionsdefinition darf gemäß der Regel mit einer Definition (One Definition Rule, ODR) nur einmal im Programm angezeigt werden.

Die erforderlichen Bestandteile einer Funktionsdeklaration lauten:

1. Der Rückgabetyp, der den Typ des Werts angibt, den die Funktion zurückgibt, oder, **`void`** Wenn kein Wert zurückgegeben wird. In c++ 11 **`auto`** ist ein gültiger Rückgabetyp, der den Compiler anweist, den Typ aus der Return-Anweisung abzuleiten. In c++ 14 `decltype(auto)` ist ebenfalls zulässig. Weitere Informationen finden Sie unten unter „Typableitung in Rückgabetypen“.

1. Der Funktionsname, der mit einem Buchstaben oder Unterstrich beginnen muss, darf keine Leerzeichen enthalten. Im Allgemeinen weisen führende Unterstriche in Standardbibliothek-Funktionsnamen auf private Memberfunktionen oder Nicht-Memberfunktionen, die nicht für die Verwendung durch Ihren Code vorgesehen sind, hin.

1. Die Parameterliste, ein durch geschweifte Klammern getrennter, kommagetrennter Satz von mindestens null Parametern, die den Typ und optional einen lokalen Namen angeben, anhand dessen die Werte im Funktionsrumpf möglicherweise aufgerufen werden.

Optionale Bestandteile einer Funktionsdeklaration sind:

1. **`constexpr`** Gibt an, dass der Rückgabewert der Funktion ein konstanter Wert ist, der zur Kompilierzeit berechnet werden kann.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Die Verknüpfungs Spezifikation **`extern`** oder **`static`** .

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Weitere Informationen finden Sie unter [Übersetzungseinheiten und Verknüpfungen](../cpp/program-and-linkage-cpp.md).

1. **`inline`**, der den Compiler anweist, jeden Aufrufe der Funktion durch den Funktionscode selbst zu ersetzen. Durch den Inlinevorgang kann die Leistung in Szenarien verbessert werden, in denen eine Funktion schnell ausgeführt und wiederholt in einem leistungskritischen Codeabschnitt aufgerufen wird.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Weitere Informationen finden Sie unter [Inline Funktionen](../cpp/inline-functions-cpp.md).

1. Ein- **`noexcept`** Ausdruck, der angibt, ob die Funktion eine Ausnahme auslösen kann. Im folgenden Beispiel löst die Funktion keine Ausnahme aus, wenn der `is_pod` Ausdruck zu ausgewertet wird **`true`** .

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Weitere Informationen finden Sie unter [`noexcept`](../cpp/noexcept-cpp.md).

1. (Nur Element Funktionen) Die CV-Qualifizierer, die angeben, ob die Funktion **`const`** oder ist **`volatile`** .

1. (Nur Element Funktionen) **`virtual`** , **`override`** oder **`final`** . **`virtual`** Gibt an, dass eine Funktion in einer abgeleiteten Klasse überschrieben werden kann. **`override`** bedeutet, dass eine Funktion in einer abgeleiteten Klasse eine virtuelle Funktion überschreibt. **`final`** bedeutet, dass eine Funktion in einer anderen abgeleiteten Klasse nicht überschrieben werden kann. Weitere Informationen finden Sie unter [virtuelle Funktionen](../cpp/virtual-functions.md).

1. (nur Element Funktionen) **`static`** die Anwendung auf eine Element Funktion bedeutet, dass die-Funktion keiner Objektinstanz der-Klasse zugeordnet ist.

1. (Nur nicht statische Member-Funktionen) Der Ref-Qualifizierer, der für den Compiler angibt, welche Überladung einer Funktion ausgewählt werden soll, wenn der implizite Objekt Parameter ( `*this` ) ein rvalue-Verweis im Vergleich zu einem Lvalue-Verweis ist. Weitere Informationen finden Sie unter [Funktions Überladung](function-overloading.md#ref-qualifiers).

Die folgende Abbildung zeigt die Teile einer Funktionsdefinition. Der schattierte Bereich ist der Funktionsrumpf.

![Teile einer Funktionsdefinition](../cpp/media/vc38ru1.gif "Teile einer Funktionsdefinition") <br/>
Teile einer Funktionsdefinition

## <a name="function-definitions"></a>Funktionsdefinitionen

Eine *Funktionsdefinition* besteht aus der Deklaration und dem Funktions Rumpf, der in geschweiften Klammern eingeschlossen ist und Variablen Deklarationen, Anweisungen und Ausdrücke enthält. Das folgende Beispiel zeigt eine komplette Funktionsdefinition:

```cpp
    int foo(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       if(strcmp(s, "default") != 0)
       {
            value = mc.do_something(i);
       }
       return value;
    }
```

Im Textteil deklarierte Variablen werden als lokale Variablen bezeichnet. Sie verlassen den Gültigkeitsbereich, wenn die Funktion beendet wird. Daher sollte eine Funktion niemals einen Verweis zu einer lokalen Variable zurückgeben!

```cpp
    MyClass& boom(int i, std::string s)
    {
       int value {i};
       MyClass mc;
       mc.Initialize(i,s);
       return mc;
    }
```

## <a name="const-and-constexpr-functions"></a>const-und constexpr-Funktionen

Sie können eine Member-Funktion als deklarieren, **`const`** um anzugeben, dass die Funktion die Werte von Datenmembern in der Klasse nicht ändern darf. Indem Sie eine Member-Funktion als deklarieren **`const`** , unterstützen Sie den Compiler beim Erzwingen von " *Konstanten-Richtigkeit*". Wenn jemand versehentlich versucht, das Objekt mithilfe einer Funktion zu ändern, die als deklariert ist **`const`** , wird ein Compilerfehler ausgelöst. Weitere Informationen finden Sie unter [konstant](const-cpp.md).

Deklarieren Sie eine Funktion, als **`constexpr`** Wenn der Wert, den Sie erzeugt, zur Kompilierzeit bestimmt werden kann. Eine constexpr-Funktion wird in der Regel schneller ausgeführt als eine reguläre Funktion. Weitere Informationen finden Sie unter [`constexpr`](constexpr-cpp.md).

## <a name="function-templates"></a>Funktionsvorlagen

Eine Funktionsvorlage ähnelt einer Klassenvorlage. Sie generiert auf Grundlage der Vorlagenargumente konkrete Funktionen. In vielen Fällen kann die Vorlage die Typargumente ableiten. Daher ist es nicht erforderlich, sie explizit anzugeben.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs;
}

auto a = Add2(3.13, 2.895); // a is a double
auto b = Add2(string{ "Hello" }, string{ " World" }); // b is a std::string
```

Weitere Informationen finden Sie unter [Funktions Vorlagen](../cpp/function-templates.md) .

## <a name="function-parameters-and-arguments"></a>Funktionsparameter und Argumente

Eine Funktion weist eine durch Kommas getrennte Liste von mindestens null Typen auf. Jede davon verfügt über einen Namen, unter dem es im Funktionsrumpf aufgerufen werden kann. Eine Funktionsvorlage kann den zusätzliche Typ- oder Wertparameter angeben. Der Aufrufer gibt Argumente weiter, bei denen es sich um konkrete Werte handelt, deren Typen mit der Parameterliste kompatibel sind.

Argumente werden standardmäßig zur Funktion nach Wert weitergegeben. Die Funktion empfängt demnach eine Kopie des weiterzugebenden Objekts. Für große Objekte kann das Erstellen einer Kopie aufwändig und nicht immer erforderlich sein. Fügen Sie dem-Parameter einen Verweis Quantifizierer hinzu, um zu bewirken, dass Argumente als Verweis übergeben werden (genauer gesagt: Lvalue-Verweis):

```cpp
void DoSomething(std::string& input){...}
```

Wenn eine Funktion ein Argument ändert, das nach Verweis weitergegeben wird, ändert sie das ursprüngliche Objekt und nicht eine lokale Kopie. Um zu verhindern, dass eine Funktion ein solches Argument ändert, qualifizieren Sie den Parameter als Konstanten&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Um Argumente explizit zu verarbeiten, die von rvalue-reference oder lvalue-Reference übergeben werden, verwenden Sie ein doppeltes kaufmännisches und-Argument für den-Parameter, um einen universellen Verweis anzugeben:

```cpp
void DoSomething(const std::string&& input){...}
```

Eine Funktion, die mit dem einzelnen Schlüsselwort **`void`** in der Parameter Deklarations Liste deklariert wird, hat keine Argumente, solange das Schlüsselwort **`void`** der erste und einzige Member der Argument Deklarations Liste ist. Argumente vom Typ an **`void`** anderer Stelle in der Liste führen zu Fehlern. Beispiel:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Beachten Sie, dass es nicht zulässig ist, ein-Argument anzugeben, **`void`** außer wie hier beschrieben, dass Typen, die vom-Typ abgeleitet sind (z. b. **`void`** Zeiger auf **`void`** und-Arrays **`void`** ), überall in der Argument Deklarations Liste vorkommen können

### <a name="default-arguments"></a>Standardargumente

Der oder die letzten Parameter in einer Funktionssignatur werden möglicherweise einem Standardargument zugewiesen. Der Aufrufer kann demnach das Argument auslassen, wenn die Funktion aufgerufen wird, es sei denn, es soll ein anderer Wert angegeben werden.

```cpp
int DoSomething(int num,
    string str,
    Allocator& alloc = defaultAllocator)
{ ... }

// OK both parameters are at end
int DoSomethingElse(int num,
    string str = string{ "Working" },
    Allocator& alloc = defaultAllocator)
{ ... }

// C2548: 'DoMore': missing default parameter for parameter 2
int DoMore(int num = 5, // Not a trailing parameter!
    string str,
    Allocator& = defaultAllocator)
{...}
```

Weitere Informationen finden Sie unter [Standardargumente](../cpp/default-arguments.md).

## <a name="function-return-types"></a>Funktionsrückgabetypen

Eine Funktion kann keine andere Funktion oder ein integriertes Array zurückgeben. Sie kann jedoch Zeiger auf diese Typen oder einen *Lambda*-Wert zurückgeben, der ein Funktions Objekt erzeugt. Mit Ausnahme dieser Fälle gibt eine Funktion möglicherweise einen Wert eines beliebigen Typs zurück, der sich im Gültigkeitsbereich befindet, oder Sie gibt keinen Wert zurück. in diesem Fall lautet der Rückgabetyp **`void`** .

### <a name="trailing-return-types"></a>Nachstehende Rückgabetypen

Ein „gewöhnlicher“ Rückgabetyp befindet sich auf der linken Seite der Funktionssignatur. Ein nach stehender *Rückgabetyp* befindet sich auf der rechten Seite der Signatur und wird dem Operator vorangestellt **`->`** . Nachstehende Rückgabetypen sind insbesondere in Funktionsvorlagen nützlich, wenn der Typ des Rückgabewerts auf Vorlagenparametern beruht.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Wenn **`auto`** in Verbindung mit einem nachfolgenden Rückgabetyp verwendet wird, dient er lediglich als Platzhalter für den Ausdruck, den der decltype-Ausdruck erzeugt, und führt nicht selbst eine Typableitung durch.

## <a name="function-local-variables"></a>Lokale Funktionsvariablen

Eine Variable, die innerhalb eines Funktions Texts deklariert wird, wird als *lokale Variable* oder einfach als *lokale*Variable bezeichnet. Nicht statische lokale Variablen sind nur innerhalb des Funktionsrumpfs sichtbar, wenn sie auf dem Stapel deklariert werden, wenn den Bereich verlässt, wenn die Funktion vorhanden ist. Wenn Sie eine lokale Variable erstellen und Sie als Wert zurückgeben, kann der Compiler normalerweise die *benannte Rückgabewert Optimierung* ausführen, um unnötige Kopiervorgänge zu vermeiden. Wenn Sie eine lokale Variable nach Verweis zurückgeben, stellt eine Compiler eine Warnung aus, da jeder Versuch durch den Aufrufer, diesen Verweis zu verwenden, erst nach der Zerstörung der lokalen Variablen auftritt.

In C++ kann eine lokale Variable als statisch deklariert werden. Die Variable ist nur innerhalb des Funktionsrumpfs sichtbar. Es ist jedoch eine einzelne Kopie der Variable für alle Instanzen der Funktion vorhanden. Lokale statische Objekte werden während der Beendigung zerstört, die von `atexit` angegeben wird. Wenn kein statisches Objekt erstellt wurde, da die Ablaufsteuerung des Programms seine Deklaration umgangen ist, wird nicht versucht, das Objekt zu zerstören.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Typableitung in Rückgabe Typen (c++ 14)

In c++ 14 können Sie verwenden, **`auto`** um den Compiler anzuweisen, den Rückgabetyp aus dem Funktions Rumpf abzuleiten, ohne einen nachfolgenden Rückgabetyp bereitstellen zu müssen. Beachten Sie, dass **`auto`** immer zu einem Rückgabewert herleitet. Verwenden Sie `auto&&` um den Compiler anzuweisen, einen Verweis abzuleiten.

In diesem Beispiel **`auto`** wird als eine nicht konstanten Wert Kopie der Summe von LHS und RHS abgeleitet.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Beachten Sie, dass **`auto`** die Konstante des Typs, den Sie herleitet, nicht beibehalten wird. Für Weiterleitungs Funktionen, deren Rückgabewert die Konstante oder die verweislichkeit der Argumente beibehalten muss, können Sie das **`decltype(auto)`** Schlüsselwort verwenden, das die **`decltype`** Typrückschluss-Regeln verwendet und alle Typinformationen beibehält. **`decltype(auto)`** kann als normaler Rückgabewert auf der linken Seite oder als nachfolgende Rückgabewert verwendet werden.

Im folgenden Beispiel (basierend auf Code aus [N3493](https://wg21.link/n3493)) wird gezeigt, wie **`decltype(auto)`** verwendet wird, um eine perfekte Weiterleitung von Funktions Argumenten in einem Rückgabetyp zu ermöglichen, der erst bekannt ist, wenn die Vorlage instanziiert wird.

```cpp
template<typename F, typename Tuple = tuple<T...>, int... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return std::forward<F>(f)(std::get<I>(std::forward<Tuple>(args))...);
}

template<typename F, typename Tuple = tuple<T...>,
    typename Indices = make_index_sequence<tuple_size<Tuple>::value >>
   decltype( auto)
    apply(F&& f, Tuple&& args)
{
    return apply_(std::forward<F>(f), std::forward<Tuple>(args), Indices());
}
```

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Zurückgeben von mehreren Werten aus einer Funktion

Es gibt verschiedene Möglichkeiten, mehr als einen Wert aus einer Funktion zurückzugeben:

1. Kapseln Sie die Werte in einer benannten Klasse oder einem Struktur Objekt. Erfordert, dass die Klassen-oder Struktur Definition für den Aufrufer sichtbar ist:

    ```cpp
    #include <string>
    #include <iostream>

    using namespace std;

    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        S s = g();
        cout << s.name << " " << s.num << endl;
        return 0;
    }
    ```

1. Gibt ein Std:: Tuple-oder Std::p Air-Objekt zurück:

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }

    int main()
    {
        auto t = f();
        cout << get<0>(t) << " " << get<1>(t) << " " << get<2>(t) << endl;

        // --or--

        int myval;
        string myname;
        double mydecimal;
        tie(myval, myname, mydecimal) = f();
        cout << myval << " " << myname << " " << mydecimal << endl;

        return 0;
    }
    ```

1. **Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): strukturierte Bindungen verwenden. Der Vorteil von strukturierten Bindungen besteht darin, dass die Variablen, die die Rückgabewerte speichern, zur gleichen Zeit initialisiert werden, in der Sie deklariert werden. Dies kann in manchen Fällen wesentlich effizienter sein. In der `auto[x, y, z] = f();` -Anweisung werden die Namen von Klammern eingeführt und initialisiert, die im Gültigkeitsbereich für den gesamten Funktionsblock liegen.

    ```cpp
    #include <tuple>
    #include <string>
    #include <iostream>

    using namespace std;

    tuple<int, string, double> f()
    {
        int i{ 108 };
        string s{ "Some text" };
        double d{ .01 };
        return { i,s,d };
    }
    struct S
    {
        string name;
        int num;
    };

    S g()
    {
        string t{ "hello" };
        int u{ 42 };
        return { t, u };
    }

    int main()
    {
        auto[x, y, z] = f(); // init from tuple
        cout << x << " " << y << " " << z << endl;

        auto[a, b] = g(); // init from POD struct
        cout << a << " " << b << endl;
        return 0;
    }
    ```

1. Zusätzlich zur Verwendung des Rückgabewerts können Sie Werte zurückgeben, indem Sie eine beliebige Anzahl von Parametern für die Verwendung von "Pass-by-Reference" definieren, damit die Funktion die Werte der vom Aufrufer bereitgestellten Objekte ändern oder initialisieren kann. Weitere Informationen finden Sie unter [Verweistyp-Funktionsargumente](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Funktionszeiger

C++ unterstützt Funktionszeiger auf die gleiche Weise wie die C-Sprache. Eine typsichere Alternative besteht jedoch darin, ein Funktionsobjekt zu verwenden.

Es wird empfohlen, **`typedef`** zum Deklarieren eines Alias für den Funktions Zeigertyp zu verwenden, wenn Sie eine Funktion deklarieren, die einen Funktions Zeigertyp zurückgibt.  Beispiel:

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Wenn dies nicht erfolgt, kann die korrekte Syntax für die Funktionsdeklaration aus der Deklaratorsyntax für den Funktionszeiger abgeleitet werden, und zwar wie folgt durch Ersetzen des Bezeichners (`fp` im obigen Beispiel) durch den Namen und die Argumentliste der Funktion:

```cpp
int (*myFunction(char* s))(int);
```

Die vorherige Deklaration entspricht der Deklaration, die oben verwendet wird **`typedef`** .

## <a name="see-also"></a>Weitere Informationen

[Funktions Überladung](../cpp/function-overloading.md)<br/>
[Funktionen mit Variablen Argument Listen](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Explizit standardmäßig standardmäßig und gelöschte Funktionen](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Argument abhängige Namenssuche (Koenig) in Funktionen](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Standardargumente](../cpp/default-arguments.md)<br/>
[Inline Funktionen](../cpp/inline-functions-cpp.md)
