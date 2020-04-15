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
ms.openlocfilehash: 1425ddebffc150158e88e44b1d2c22e3f85e5a31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375737"
---
# <a name="functions-c"></a>Funktionen (C++)

Eine Funktion ist ein Codeblock, der einige Vorgänge ausführt. Eine Funktion kann optional Eingabeparameter definieren, die Aufrufern ermöglichen, Argumente in die Funktion weiterzugeben. Eine Funktion kann einen Wert optional als Ausgabe zurückgeben. Funktionen sind für das Kapseln allgemeiner Vorgänge in einem einzelnen wiederverwendbaren Block nützlich, und zwar ideal unter Verwendung eines Namens, der deutlich das beschreibt, was die Funktion vornimmt. Die folgende Funktion akzeptiert zwei ganze Zahlen von einem Aufrufer und gibt deren Summe zurück. *a* und *b* sind *Parameter* vom Typ **int**.

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Die Funktion kann von einer beliebigen Anzahl von Stellen im Programm aufgerufen oder *aufgerufen*werden. Die Werte, die an die Funktion übergeben werden, sind die *Argumente*, deren Typen mit den Parametertypen in der Funktionsdefinition kompatibel sein müssen.

```cpp
int main()
{
    int i = sum(10, 32);
    int j = sum(i, 66);
    cout << "The value of j is" << j << endl; // 108
}
```

Es gibt keine praktische Begrenzung für die Funktionslänge, jedoch angemessene Entwurfsziele für Funktionen, die eine einzelne klar definierte Aufgabe ausführen. Komplexe Algorithmen sollten möglichst in leicht verständliche einfachere Funktionen aufgeschlüsselt werden.

Im Klassenbereich definierte Funktionen werden als Memberfunktionen bezeichnet. In C++ kann eine Funktion im Gegensatz zu anderen Sprachen auch im Namespacebereich (einschließlich des impliziten globalen Namespace) definiert werden. Solche Funktionen werden *als freie Funktionen* oder *Nicht-Member-Funktionen*bezeichnet; sie werden ausgiebig in der Standardbibliothek verwendet.

Funktionen können *überladen*sein, was bedeutet, dass verschiedene Versionen einer Funktion denselben Namen haben können, wenn sie sich durch die Anzahl und/oder den Typ der formalen Parameter unterscheiden. Weitere Informationen finden Sie unter [Funktionsüberladung](../cpp/function-overloading.md).

## <a name="parts-of-a-function-declaration"></a>Bestandteile einer Funktionsdeklaration

Eine minimale *Funktionsdeklaration* besteht aus dem Rückgabetyp, dem Funktionsnamen und der Parameterliste (die leer sein kann) zusammen mit optionalen Schlüsselwörtern, die zusätzliche Anweisungen für den Compiler bereitstellen. Das folgende Beispiel ist eine Funktionsdeklaration:

```cpp
int sum(int a, int b);
```

Eine Funktionsdefinition besteht aus einer Deklaration plus dem *Text*, der den gesamten Code zwischen den geschweiften Klammern ist:

```cpp
int sum(int a, int b)
{
    return a + b;
}
```

Eine Funktionsdeklaration, auf die ein Semikolon folgt, wird möglicherweise an mehreren Stellen in einem Programm angezeigt. Sie muss vor dem Aufrufen dieser Funktion in jeder Übersetzungseinheit angezeigt werden. Die Funktionsdefinition darf gemäß der Regel mit einer Definition (One Definition Rule, ODR) nur einmal im Programm angezeigt werden.

Die erforderlichen Bestandteile einer Funktionsdeklaration lauten:

1. Der Rückgabetyp, der den Typ des von der Funktion zurückgegebenen Werts angibt, oder **void,** wenn kein Wert zurückgegeben wird. In C++11 ist **auto** ein gültiger Rückgabetyp, der den Compiler anweist, den Typ aus der rückgabeanweisung abzuleiten. In C++14 ist „decltype(auto)“ ebenfalls zulässig. Weitere Informationen finden Sie unten unter „Typableitung in Rückgabetypen“.

1. Der Funktionsname, der mit einem Buchstaben oder Unterstrich beginnen muss, darf keine Leerzeichen enthalten. Im Allgemeinen weisen führende Unterstriche in Standardbibliothek-Funktionsnamen auf private Memberfunktionen oder Nicht-Memberfunktionen, die nicht für die Verwendung durch Ihren Code vorgesehen sind, hin.

1. Die Parameterliste, ein durch geschweifte Klammern getrennter, kommagetrennter Satz von mindestens null Parametern, die den Typ und optional einen lokalen Namen angeben, anhand dessen die Werte im Funktionsrumpf möglicherweise aufgerufen werden.

Optionale Bestandteile einer Funktionsdeklaration sind:

1. `constexpr`. Gibt an, dass es sich beim Rückgabewert der Funktion um einen konstanten Wert handelt, der zur Kompilierungszeit berechnet werden kann.

    ```cpp
    constexpr float exp(float x, int n)
    {
        return n == 0 ? 1 :
            n % 2 == 0 ? exp(x * x, n / 2) :
            exp(x * x, (n - 1) / 2) * x;
    };
    ```

1. Die Verknüpfungsspezifikation, **extern** oder **statisch.**

    ```cpp
    //Declare printf with C linkage.
    extern "C" int printf( const char *fmt, ... );

    ```

   Weitere Informationen finden Sie unter [Übersetzungseinheiten und Verknüpfung](../cpp/program-and-linkage-cpp.md).

1. **inline**, in der der Compiler angewiesen wird, jeden Aufruf der Funktion durch den Funktionscode selbst zu ersetzen. Durch den Inlinevorgang kann die Leistung in Szenarien verbessert werden, in denen eine Funktion schnell ausgeführt und wiederholt in einem leistungskritischen Codeabschnitt aufgerufen wird.

    ```cpp
    inline double Account::GetBalance()
    {
        return balance;
    }
    ```

   Weitere Informationen finden Sie unter [Inlinefunktionen](../cpp/inline-functions-cpp.md).

1. Ein `noexcept` Ausdruck, der angibt, ob die Funktion eine Ausnahme auslösen kann. Im folgenden Beispiel löst die Funktion keine `is_pod` Ausnahme aus, wenn der Ausdruck als **true**ausgewertet wird.

    ```cpp
    #include <type_traits>

    template <typename T>
    T copy_object(T& obj) noexcept(std::is_pod<T>) {...}
    ```

   Weitere Informationen finden Sie unter [noexcept](../cpp/noexcept-cpp.md).

1. (Nur Mitgliedsfunktionen) Die cv-qualifizierer, die angeben, ob die Funktion **const** oder **volatile**ist.

1. (Nur Mitgliedsfunktionen) **virtual** `override`, `final`oder . **virtual** gibt an, dass eine Funktion in einer abgeleiteten Klasse überschrieben werden kann. `override` bedeutet, dass eine Funktion in einer abgeleiteten Klasse eine virtuelle Funktion überschreibt. `final` bedeutet, dass eine Funktion in keiner weiteren abgeleiteten Klasse überschrieben werden kann. Weitere Informationen finden Sie unter [Virtuelle Funktionen](../cpp/virtual-functions.md).

1. (nur Memberfunktionen) **statisch** angewendet auf eine Memberfunktion bedeutet, dass die Funktion keiner Objektinstanz der Klasse zugeordnet ist.

1. (Nur nicht statische Memberfunktionen) Der ref-Qualifizierer, der dem Compiler angibt, welche Überladung\*einer Funktion zu wählen ist, wenn der implizite Objektparameter (dies) ein rvalue-Verweis im Vergleich zu einem lvalue-Verweis ist. Weitere Informationen finden Sie unter [Funktionsüberladung](function-overloading.md#ref-qualifiers).

Die folgende Abbildung zeigt die Teile einer Funktionsdefinition. Der schattierte Bereich ist der Funktionsrumpf.

![Teile einer Funktionsdefinition](../cpp/media/vc38ru1.gif "Teile einer Funktionsdefinition") <br/>
Teile einer Funktionsdefinition

## <a name="function-definitions"></a>Funktionsdefinitionen

Eine *Funktionsdefinition* besteht aus der Deklaration und dem Funktionstext, die in geschweifte Klammern eingeschlossen sind und Variablendeklarationen, Anweisungen und Ausdrücke enthalten. Das folgende Beispiel zeigt eine vollständige Funktionsdefinition:

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

## <a name="const-and-constexpr-functions"></a>const- und constexpr-Funktionen

Sie können eine Memberfunktion als **const** deklarieren, um anzugeben, dass die Funktion die Werte von Datenmembern in der Klasse nicht ändern darf. Indem Sie eine Memberfunktion als **const**deklarieren, helfen Sie dem Compiler, *const-correctness*zu erzwingen. Wenn jemand irrtümlicherweise versucht, das Objekt mithilfe einer funktion zu ändern, die als **const**deklariert wurde, wird ein Compilerfehler ausgelöst. Weitere Informationen finden Sie unter [const](const-cpp.md).

Deklarieren `constexpr` Sie eine Funktion, wenn der erzeugte Wert möglicherweise zur Kompilierungszeit bestimmt werden kann. Eine constexpr-Funktion wird in der Regel schneller ausgeführt als eine reguläre Funktion. Weitere Informationen finden Sie unter [constexpr](constexpr-cpp.md).

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

Weitere Informationen finden Sie unter [Funktionsvorlagen](../cpp/function-templates.md)

## <a name="function-parameters-and-arguments"></a>Funktionsparameter und Argumente

Eine Funktion weist eine durch Kommas getrennte Liste von mindestens null Typen auf. Jede davon verfügt über einen Namen, unter dem es im Funktionsrumpf aufgerufen werden kann. Eine Funktionsvorlage kann den zusätzliche Typ- oder Wertparameter angeben. Der Aufrufer gibt Argumente weiter, bei denen es sich um konkrete Werte handelt, deren Typen mit der Parameterliste kompatibel sind.

Argumente werden standardmäßig zur Funktion nach Wert weitergegeben. Die Funktion empfängt demnach eine Kopie des weiterzugebenden Objekts. Für große Objekte kann das Erstellen einer Kopie aufwändig und nicht immer erforderlich sein. Um zu bewirken, dass Argumente als Verweis übergeben werden (insbesondere lvalue-Referenz), fügen Sie dem Parameter einen Referenzquantifier hinzu:

```cpp
void DoSomething(std::string& input){...}
```

Wenn eine Funktion ein Argument ändert, das nach Verweis weitergegeben wird, ändert sie das ursprüngliche Objekt und nicht eine lokale Kopie. Um zu verhindern, dass eine Funktion ein solches Argument ändert, qualifizieren Sie den Parameter als const&:

```cpp
void DoSomething(const std::string& input){...}
```

**C++ 11:**  Um Argumente explizit zu behandeln, die von rvalue-reference oder lvalue-reference übergeben werden, verwenden Sie ein Double-ampersand für den Parameter, um einen universellen Verweis anzugeben:

```cpp
void DoSomething(const std::string&& input){...}
```

Eine Funktion, die mit dem einzelnen Schlüsselwort **void** in der Parameterdeklarationsliste deklariert ist, benötigt keine Argumente, solange das Schlüsselwort **void** das erste und einzige Element der Argumentdeklarationsliste ist. Argumente des Typs **void** an anderer Stelle in der Liste führen zu Fehlern. Beispiel:

```cpp

// OK same as GetTickCount()
long GetTickCount( void );
```

Beachten Sie, dass, obwohl es ungültig ist, ein **void-Argument** anzugeben, außer wie hier beschrieben, Typen, die vom Typ **void** abgeleitet sind (z. B. Zeiger auf **void** und Arrays von **void),** überall in der Argumentdeklarationsliste angezeigt werden können.

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

Eine Funktion gibt möglicherweise keine andere Funktion oder ein integriertes Array zurück. Es kann jedoch Zeiger auf diese Typen oder einen *Lambda*zurückgeben, der ein Funktionsobjekt erzeugt. Mit Ausnahme dieser Fälle kann eine Funktion einen Wert eines beliebigen Typs zurückgeben, der sich im Gültigkeitsbereich befindet, oder sie gibt keinen Wert zurück, in diesem Fall ist der Rückgabetyp **void**.

### <a name="trailing-return-types"></a>Nachstehende Rückgabetypen

Ein „gewöhnlicher“ Rückgabetyp befindet sich auf der linken Seite der Funktionssignatur. Ein *nachgestellter Rückgabetyp* befindet sich auf der rechten Seite der Signatur und wird durch den Operator -> vorangestellt. Nachstehende Rückgabetypen sind insbesondere in Funktionsvorlagen nützlich, wenn der Typ des Rückgabewerts auf Vorlagenparametern beruht.

```cpp
template<typename Lhs, typename Rhs>
auto Add(const Lhs& lhs, const Rhs& rhs) -> decltype(lhs + rhs)
{
    return lhs + rhs;
}
```

Wenn **auto** in Verbindung mit einem nachgestellten Rückgabetyp verwendet wird, dient es nur als Platzhalter für das, was der decltype-Ausdruck erzeugt, und führt selbst keinen Typabzug durch.

## <a name="function-local-variables"></a>Lokale Funktionsvariablen

Eine Variable, die innerhalb eines Funktionstexts deklariert wird, wird als *lokale Variable* oder einfach als *lokale*. Nicht statische lokale Variablen sind nur innerhalb des Funktionsrumpfs sichtbar, wenn sie auf dem Stapel deklariert werden, wenn den Bereich verlässt, wenn die Funktion vorhanden ist. Wenn Sie eine lokale Variable erstellen und nach Wert zurückgeben, kann der Compiler in der Regel die *benannte Rückgabewertoptimierung* durchführen, um unnötige Kopiervorgänge zu vermeiden. Wenn Sie eine lokale Variable nach Verweis zurückgeben, stellt eine Compiler eine Warnung aus, da jeder Versuch durch den Aufrufer, diesen Verweis zu verwenden, erst nach der Zerstörung der lokalen Variablen auftritt.

In C++ kann eine lokale Variable als statisch deklariert werden. Die Variable ist nur innerhalb des Funktionsrumpfs sichtbar. Es ist jedoch eine einzelne Kopie der Variable für alle Instanzen der Funktion vorhanden. Lokale statische Objekte werden während der Beendigung zerstört, die von `atexit` angegeben wird. Wenn kein statisches Objekt erstellt wurde, da die Ablaufsteuerung des Programms seine Deklaration umgangen ist, wird nicht versucht, das Objekt zu zerstören.

## <a name="type-deduction-in-return-types-c14"></a><a name="type_deduction"></a>Typabzug in Reklamattypen (C++14)

In C++14 können Sie **den** Compiler automatisch anweisen, den Rückgabetyp aus dem Funktionstext abzuleiten, ohne einen nachfolgenden Rückgabetyp angeben zu müssen. Beachten Sie, dass **auto** immer zu einem Return-by-Wert ableitet. Verwenden Sie `auto&&` um den Compiler anzuweisen, einen Verweis abzuleiten.

In diesem Beispiel wird **auto** als Nicht-const-Wertkopie der Summe von lhs und rhs abgeleitet.

```cpp
template<typename Lhs, typename Rhs>
auto Add2(const Lhs& lhs, const Rhs& rhs)
{
    return lhs + rhs; //returns a non-const object by value
}
```

Beachten Sie, dass **auto** die Konsistenz des typs, den es ableitet, nicht beibehält. Für Weiterleitungsfunktionen, deren Rückgabewert die Konsistenz oder Ref-ness seiner Argumente beibehalten muss, können Sie das Schlüsselwort **decltype(auto)** verwenden, das die **Decltype-Typ-Inferenzregeln** verwendet und alle Typinformationen beibehält. **decltype(auto)** kann als normaler Rückgabewert auf der linken Seite oder als nachgestellter Rückgabewert verwendet werden.

Das folgende Beispiel (basierend auf Code aus [N3493](https://wg21.link/n3493)) zeigt, dass **decltype(auto)** verwendet wird, um die perfekte Weiterleitung von Funktionsargumenten in einem Rückgabetyp zu ermöglichen, der erst bekannt ist, wenn die Vorlage instanziiert wurde.

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

## <a name="returning-multiple-values-from-a-function"></a><a name="multi_val"></a>Zurückgeben mehrerer Werte aus einer Funktion

Es gibt verschiedene Möglichkeiten, mehr als einen Wert von einer Funktion zurückzugeben:

1. Kapseln Sie die Werte in einer benannten Klasse oder einem Strukturobjekt. Erfordert, dass die Klassen- oder Strukturdefinition für den Aufrufer sichtbar ist:

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

1. Geben Sie ein std::tupel- oder std::pair-Objekt zurück:

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

1. **Visual Studio 2017 Version 15.3 und höher** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Verwenden Sie strukturierte Bindungen. Der Vorteil strukturierter Bindungen besteht darin, dass die Variablen, die die Rückgabewerte speichern, gleichzeitig initialisiert werden, wenn sie deklariert werden, was in einigen Fällen wesentlich effizienter sein kann. In dieser Anweisung`auto[x, y, z] = f();`-- -- führen die Klammern Namen ein und initialisieren sie, die für den gesamten Funktionsbaustein im Gültigkeitsbereich stehen.

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

1. Zusätzlich zur Verwendung des Rückgabewerts selbst können Sie Werte "zurückgeben", indem Sie eine beliebige Anzahl von Parametern definieren, um Pass-by-Verweis zu verwenden, damit die Funktion die Werte von Objekten ändern oder initialisieren kann, die der Aufrufer bereitstellt. Weitere Informationen finden Sie unter [Referenztypfunktionsargumente](reference-type-function-arguments.md).

## <a name="function-pointers"></a>Funktionszeiger

C++ unterstützt Funktionszeiger auf die gleiche Weise wie die C-Sprache. Eine typsichere Alternative besteht jedoch darin, ein Funktionsobjekt zu verwenden.

Es wird empfohlen, **typedef** zum Deklarieren eines Alias für den Funktionszeigertyp zu verwenden, wenn eine Funktion deklariert wird, die einen Funktionszeigertyp zurückgibt.  Beispiel:

```cpp
typedef int (*fp)(int);
fp myFunction(char* s); // function returning function pointer
```

Wenn dies nicht erfolgt, kann die korrekte Syntax für die Funktionsdeklaration aus der Deklaratorsyntax für den Funktionszeiger abgeleitet werden, und zwar wie folgt durch Ersetzen des Bezeichners (`fp` im obigen Beispiel) durch den Namen und die Argumentliste der Funktion:

```cpp
int (*myFunction(char* s))(int);
```

Die vorhergehende Deklaration gleicht der Deklaration oben, die "typedef" verwendet.

## <a name="see-also"></a>Siehe auch

[Funktionsüberladung](../cpp/function-overloading.md)<br/>
[Funktionen mit Variablenargumentlisten](../cpp/functions-with-variable-argument-lists-cpp.md)<br/>
[Explizit vorgegebene und gelöschte Funktionen](../cpp/explicitly-defaulted-and-deleted-functions.md)<br/>
[Argumentbezogene Namenssuche (Koenig) in Funktionen](../cpp/argument-dependent-name-koenig-lookup-on-functions.md)<br/>
[Standardargumente](../cpp/default-arguments.md)<br/>
[Inlinefunktionen](../cpp/inline-functions-cpp.md)
