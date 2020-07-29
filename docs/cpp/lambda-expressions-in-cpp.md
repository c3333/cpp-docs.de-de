---
title: Lambda-Ausdrücke in C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 6fcc26c3ed86c86264773a70ac16501c102e1861
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213332"
---
# <a name="lambda-expressions-in-c"></a>Lambda-Ausdrücke in C++

In c++ 11 und höher ist ein Lambda Ausdruck –, der häufig als *Lambda*bezeichnet wird – eine bequeme Methode zum Definieren eines anonymen Funktions Objekts ( *Closure*) direkt an der Stelle, an der es aufgerufen oder als Argument an eine Funktion weitergeleitet wird. Lambda-Ausdrücke werden in der Regel verwendet, um ein paar Codezeilen zu kapseln, die an Algorithmen oder asynchrone Methoden übergeben werden. Dieser Artikel definiert, was Lambdas sind, vergleicht sie mit anderen Programmierverfahren, beschreibt ihre Vorteile und bietet ein grundlegendes Beispiel.

## <a name="related-topics"></a>Verwandte Themen

- [Lambda-Ausdrücke im Vergleich zu Funktions Objekten](lambda-expression-syntax.md)
- [Arbeiten mit Lambda-Ausdrücken](examples-of-lambda-expressions.md)
- [constexpr-Lambdaausdrücke](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Bestandteile eines Lambda-Ausdrucks

Der ISO C++-Standard zeigt einen einfachen Lambda-Ausdruck, der als drittes Argument an die `std::sort()`-Funktion übergeben wird:

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

In dieser Abbildung werden die Bestandteile eines Lambda-Ausdrucks dargestellt:

![Strukturelle Elemente eines Lambda-Ausdrucks](../cpp/media/lambdaexpsyntax.png "Strukturelle Elemente eines Lambda-Ausdrucks")

1. *Capture-Klausel* (auch bekannt als *Lambda-Introducer* in der C++-Spezifikation)

1. *Parameterliste* Optionale. (Auch als *Lambda Deklarator*bezeichnet)

1. *änderbare Spezifikation* Optionale.

1. *Exception-Spezifikation* Optionale.

1. *Trailing-Rückgabetyp* Optionale.

1. *Lambda-Text*.

### <a name="capture-clause"></a>Erfassungsklausel

Ein Lambda-Ausdruck kann neue Variablen in seinen Text einfügen (in **c++ 14**), und er kann auch auf Variablen aus dem umgebenden Bereich zugreifen oder diese *erfassen*. Ein Lambda-Ausdruck beginnt mit der Capture *-Klausel (Lambda-Introduction* in der Standard Syntax), die angibt, welche Variablen aufgezeichnet werden und ob es sich um einen Wert oder einen Verweis handelt. Auf Variablen mit dem kaufmännischen Und-Zeichen (`&`) als Präfix erfolgt der Zugriff nach Verweis, und auf Variablen ohne dieses Präfix wird nach Wert zugegriffen.

Eine leere Erfassungsklausel (`[ ]`) gibt an, dass der Lambda-Text auf keine Variablen im einschließenden Bereich zugreift.

Sie können den Standard Erfassungs Modus (*Capture-default* in der Standard Syntax) verwenden, um anzugeben, wie externe Variablen aufgezeichnet werden sollen, auf die im Lambda verwiesen wird: `[&]` bedeutet, dass alle Variablen, auf die Sie verweisen, als Verweis aufgezeichnet werden, und bedeutet, dass `[=]` Sie nach Wert aufgezeichnet werden. Sie können einen Standarderfassungsmodus verwenden, und dann den entgegengesetzten Modus explizit für bestimmte Variablen angeben. Wenn beispielsweise der Lambda-Text auf die externe Variable `total` nach Wert zugreift und auf die externe Variable `factor` nach Wert, dann sind die folgenden Erfassungsklauseln gleichwertig:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Nur Variablen, die im Lambda-Ausdruck erwähnt werden, werden aufgezeichnet, wenn eine Capture-Default-Einstellung verwendet wird.

Wenn eine Capture-Klausel einen Capture-Default-Wert enthält `&` , `identifier` kann No in einer `capture` dieser Erfassungs Klausel das Formular haben `& identifier` . Wenn die Capture-Klausel einen Capture-Default-Wert enthält `=` , kann auch keine `capture` dieser Aufzeichnungs Klauseln das Formular haben `= identifier` . Ein Bezeichner oder **`this`** darf nicht mehr als einmal in einer Capture-Klausel vorkommen. Der folgende Codeausschnitt veranschaulicht einige Beispiele.

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

Eine Erfassung, gefolgt von einem Ellipsen, ist eine Paket Erweiterung, wie in diesem Beispiel für eine [Variadic-Vorlage](../cpp/ellipses-and-variadic-templates.md) gezeigt:

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Wenn Sie Lambda-Ausdrücke im Text einer Klassenmethode verwenden möchten, übergeben Sie den **`this`** Zeiger auf die Erfassungs Klausel, um den Zugriff auf die Methoden und Datenmember der einschließenden Klasse bereitzustellen.

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): der **`this`** Zeiger kann nach Wert aufgezeichnet werden, indem **`*this`** in der Erfassungs Klausel angegeben wird. Die Erfassung nach Wert bedeutet, dass der gesamte *Abschluss*, bei dem es sich um das anonyme Funktions Objekt handelt, das den Lambda-Ausdruck einschließt, an jede Aufruf Site kopiert wird, in der der Lambda-Ausdruck aufgerufen wird. Die Erfassung nach Wert ist nützlich, wenn der Lambda-Ausdruck in parallelen oder asynchronen Vorgängen ausgeführt wird, insbesondere bei bestimmten Hardwarearchitekturen, z. b. NUMA.

Ein Beispiel für die Verwendung von Lambda-Ausdrücken mit Klassen Methoden finden Sie unter "Beispiel: Verwenden eines Lambda-Ausdrucks in einer Methode" unter [Beispiele für Lambda-Ausdrücke](../cpp/examples-of-lambda-expressions.md).

Wenn Sie die Erfassungsklausel verwenden, sollten Sie diese wichtigen Punkte beachten, insbesondere wenn Sie Lambdas mit Multithreading verwenden:

- Verweiserfassungen können im Gegensatz zu Werterfassungen dazu verwendet werden, um Variablen outside zu ändern. ( **`mutable`** ermöglicht, dass Kopien geändert werden, aber keine Originale.)

- Verweiserfassungen können im Gegensatz zu Werterfassungen Änderungen von Variablen outside wiederspiegeln.

- Verweiserfassungen führen eine Lebenszeitabhängigkeit ein, während Werterfassungen keine Lebenszeitabhängigkeiten haben. Dies ist besonders beim asynchronen Ausführen von Lambda-Ausdrücken von Bedeutung. Beim Erfassen einer lokalen Variablen in einem asynchronem Lambda-Ausdruck ist die Variable höchstwahrscheinlich beim Ausführen des Lambdas nicht verfügbar und es tritt eine Zugriffsverletzung zur Laufzeit auf.

### <a name="generalized-capture-c-14"></a>Generalisierte Erfassung (C++14)

Neue Variablen können in C++14 in der Erfassungsklausel eingeführt und initialisiert werden, ohne dass diese Variablen im Bereich der Lambdafunktion vorhanden sein müssen. Die Initialisierung kann mit einem beliebigen Ausdruck ausgedrückt werden; der Typ der neuen Variablen wird von dem durch den Ausdruck genierten Typ abgeleitet. Ein Vorteil dieser Funktion ist, dass Sie in C++14 Variablen, die nur verschoben werden können, (z. B. std::unique_ptr) aus dem umgebenden Bereich erfassen und in einem Lambda-Ausdruck verwenden können.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Parameterliste

Neben dem Erfassen von Variablen werden in einem Lambda-Ausdruck Eingabeparameter akzeptiert. Eine Parameterliste (*Lambda Deklarator* in der Standard Syntax) ist optional und ähnelt in den meisten Aspekten der Parameterliste für eine Funktion.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

In **c++ 14**können Sie das- **`auto`** Schlüsselwort als Typspezifizierer verwenden, wenn der Parametertyp generisch ist. Das weist den Compiler an, den Funktionsaufrufoperator als Vorlage zu erstellen. Jede Instanz von **`auto`** in einer Parameterliste entspricht einem eindeutigen Typparameter.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Ein Lambdaausdruck kann einen anderen Lambdaausdruck als Argument übernehmen. Weitere Informationen finden Sie unter "Lambda-Ausdrücke höherer Ordnung" im Thema [Beispiele für Lambda-Ausdrücke](../cpp/examples-of-lambda-expressions.md).

Da eine Parameterliste optional ist, können Sie die leeren Klammern weglassen, wenn Sie keine Argumente an den Lambda-Ausdruck übergeben und der Lambda-Deklarator keine *Exception-Specification*, *Trailing-Return-Type*oder enthält **`mutable`** .

### <a name="mutable-specification"></a>Änderbare Spezifikation

In der Regel ist der Funktions Aufrufoperator eines Lambda-Werts konstant, aber mit der Verwendung des- **`mutable`** Schlüssel Worts wird dies abgebrochen. Er erzeugt keine änderbaren Datenmember. Die änderbare Spezifikation aktiviert den Text eines Lambdaausdrucks, um Variablen zu ändern, die als Wert erfasst werden. Einige der Beispiele weiter unten in diesem Artikel veranschaulichen die Verwendung von **`mutable`** .

### <a name="exception-specification"></a>Ausnahmespezifikation

Sie können die **`noexcept`** Ausnahme Spezifikation verwenden, um anzugeben, dass der Lambda-Ausdruck keine Ausnahmen auslöst. Wie bei normalen Funktionen generiert der Microsoft C++-Compiler eine Warnung [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) wenn ein Lambda-Ausdruck die **`noexcept`** Ausnahme Spezifikation deklariert und der Lambda-Text eine Ausnahme auslöst, wie hier gezeigt:

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

Weitere Informationen finden Sie unter [Ausnahme Spezifikationen (Throw)](../cpp/exception-specifications-throw-cpp.md).

### <a name="return-type"></a>Rückgabetyp

Der Rückgabetyp von Lambda-Ausdrücken wird automatisch hergeleitet. Sie müssen das-Schlüsselwort nicht verwenden, [`auto`](../cpp/auto-cpp.md) es sei denn, Sie geben einen *nachfolgenden Rückgabetyp*an. Der *nachfolgende-Rückgabetyp* ähnelt dem Rückgabetyp Teil einer normalen Methode oder Funktion. Der Rückgabetyp muss jedoch der Parameterliste folgen, und Sie müssen das Schlüsselwort "Trailing-Return-Type" **`->`** vor dem Rückgabetyp einschließen.

Sie können den Rückgabetyp eines Lambda-Ausdrucks weglassen, wenn der Lambda-Text nur eine einzelne Return-Anweisung enthält oder der Lambda-Ausdruck keinen Wert zurückgibt. Wenn der Lambda-Text aus einer einzelnen Rückgabeanweisung besteht, leitet der Compiler den Rückgabetyp vom Typ des Rückgabeausdrucks ab. Andernfalls leitet der Compiler den Rückgabetyp als ab **`void`** . Betrachten Sie die folgenden Beispiele von Codeausschnitten, die dieses Prinzip veranschaulichen.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Ein Lambdaausdruck kann einen anderen Lambdaausdruck als Rückgabewert erzeugen. Weitere Informationen finden Sie unter "Lambda-Ausdrücke höherer Ordnung" unter [Beispiele für Lambda-Ausdrücke](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Lambda-Text

Der Lambda-Text (*Verbund Anweisung* in der Standard Syntax) eines Lambda-Ausdrucks kann alles enthalten, was der Text einer gewöhnlichen Methode oder Funktion enthalten kann. Der Text einer gewöhnlichen Funktion und eines Lambdaausdrucks kann auf die folgenden Variablenarten zugreifen:

- Aus dem einschließenden Bereich erfasste Variablen, wie zuvor beschrieben.

- Parameter

- Lokal deklarierte Variablen

- Klassendatenmember, wenn Sie in einer Klasse deklariert und **`this`** aufgezeichnet werden

- Jede beliebige Variable mit statischer Speicherdauer (z. B. globale Variablen)

Das folgende Beispiel enthält einen Lambdaausdruck, welcher explizit die Variable `n` nach ihrem Wert erfasst und implizit die Variable `m` als Verweis erfasst:

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

Da die Variable `n` als Wert erfasst wird, bleibt der Wert `0` nach dem Aufruf des Lambda-Ausdrucks erhalten. Die **`mutable`** Spezifikation ermöglicht das `n` ändern innerhalb des Lambda-Ausdrucks.

Obwohl ein Lambdaausdruck nur Variablen mit automatischer Speicherdauer aufzeichnen kann, können Sie Variablen verwenden, die eine statische Speicherdauer im Text eines Lambdaausdrucks aufweisen. Im folgenden Beispiel wird die Funktion `generate` und ein Lambdaausdruck verwendet, um jedem Element in einem `vector`-Objekt einen Wert zuzuweisen. Der Lambda-Ausdruck ändert die statische Variable, um den Wert des nächsten Elements zu generieren.

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

Weitere Informationen finden Sie unter [generieren](../standard-library/algorithm-functions.md#generate)von.

Im folgenden Codebeispiel wird die-Funktion aus dem vorherigen Beispiel verwendet, und es wird ein Beispiel eines Lambda-Ausdrucks hinzugefügt, der den C++-Standard Bibliotheks Algorithmus verwendet `generate_n` . Dieser Lambdaausdruck weist ein Element eines `vector`-Objekts der Summe der vorangehenden zwei Elemente zu. Das **`mutable`** -Schlüsselwort wird verwendet, sodass der Text des Lambda-Ausdrucks seine Kopien der externen Variablen und ändern kann `x` `y` , die vom Lambda-Ausdruck als Wert erfasst werden. Da der Lambdaausdruck die originalen Variablen `x` und `y` als Wert erfasst, bleiben die Werte `1`, nachdem das Lambda ausgeführt wird.

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

Weitere Informationen finden Sie unter [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="constexpr-lambda-expressions"></a>`constexpr`Lambda-Ausdrücke

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): ein Lambda-Ausdruck kann als **`constexpr`** oder in einem konstanten Ausdruck verwendet werden, wenn die Initialisierung jedes Datenmembers, den es erfasst oder einführt, innerhalb eines konstanten Ausdrucks zulässig ist.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Ein Lambda-Ausdruck ist implizit, **`constexpr`** wenn sein Ergebnis den Anforderungen einer **`constexpr`** Funktion entspricht:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Wenn ein Lambda implizit oder explizit ist **`constexpr`** , erzeugt die Konvertierung in einen Funktionszeiger eine **`constexpr`** Funktion:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft-spezifisch

Lambdas werden in den folgenden Common Language Runtime (CLR) verwalteten Entitäten nicht unterstützt: **`ref class`** , **`ref struct`** , **`value class`** oder **`value struct`** .

Wenn Sie einen Microsoft-spezifischen Modifizierer, z. b. [`__declspec`](../cpp/declspec.md) , verwenden, können Sie ihn direkt nach dem – in einen Lambda Ausdruck einfügen `parameter-declaration-clause` :

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Informationen dazu, ob ein Modifizierer von Lambdas unterstützt wird, finden Sie im Artikel über den [Microsoft-spezifischen Modifizierer der-](../cpp/microsoft-specific-modifiers.md) Dokumentation.

Zusätzlich zu den Standard mäßigen Lambda-Funktionen von c++ 11 unterstützt Visual Studio Zustands lose Lambdas, die zu Funktions Zeigern konvertiert werden können, die beliebige Aufruf Konventionen verwenden.

## <a name="see-also"></a>Siehe auch

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Funktions Objekte in der C++-Standard Bibliothek](../standard-library/function-objects-in-the-stl.md)<br/>
[Funktionsaufrufe](../cpp/function-call-cpp.md)<br/>
[`for_each`](../standard-library/algorithm-functions.md#for_each)
