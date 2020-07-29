---
title: auto (C++
ms.date: 12/10/2019
f1_keywords:
- auto_CPP
- auto
helpviewer_keywords:
- auto keyword [C++]
ms.assetid: e9d495d7-601c-4547-b897-998389a311f4
ms.openlocfilehash: 675f6919b6804cfb1d2c5395d046cb5fa39e625d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229193"
---
# <a name="auto-c"></a>`auto` (C++)

Leitet den Typ einer deklarierten Variable vom entsprechenden Initialisierungsausdruck ab.

> [!NOTE]
> Der C++-Standard definiert eine ursprüngliche und eine überarbeitete Bedeutung für dieses Schlüsselwort. Vor Visual Studio 2010 deklariert das **`auto`** Schlüsselwort eine Variable in der *automatischen* Speicher Klasse, d. h. eine Variable, die über eine lokale Lebensdauer verfügt. Ab Visual Studio 2010 deklariert das- **`auto`** Schlüsselwort eine Variable, deren Typ aus dem Initialisierungs Ausdruck in der Deklaration abgeleitet wird. Die [ `/Zc:auto`&#91;-&#93;-](../build/reference/zc-auto-deduce-variable-type.md) Compileroption steuert die Bedeutung des- **`auto`** Schlüssel Worts.

## <a name="syntax"></a>Syntax

> **`auto`***declarator* *deklaratorinitialisierer***`;`**

> **`[](auto`***param1* **`, auto`** *Param2***`) {};`**

## <a name="remarks"></a>Bemerkungen

Das- **`auto`** Schlüsselwort weist den Compiler an, den Initialisierungs Ausdruck einer deklarierten Variable oder einen Lambda-Ausdrucks Parameter zu verwenden, um den Typ abzuleiten.

Es wird empfohlen, dass Sie das- **`auto`** Schlüsselwort in den meisten Situationen verwenden – es sei denn, Sie möchten eine Konvertierung –, weil es diese Vorteile bietet:

- **Stabilität:** , Wenn der Typ des Ausdrucks geändert wird – dies schließt ein, wenn ein Funktions Rückgabetyp geändert wird – er funktioniert einfach.

- **Leistung:** Sie sind sicher, dass keine Konvertierung erfolgt.

- **Benutzerfreundlichkeit:** Sie müssen sich keine Gedanken über Rechtschreib Probleme mit Typnamen und Typos machen.

- **Effizienz:** Ihre Codierung kann effizienter sein.

Konvertierungs Fälle, in denen Sie möglicherweise nicht verwenden möchten **`auto`** :

- Wenn Sie einen ganz bestimmten Typ benötigen, und nichts anderes infrage kommt.

- Hilfstypen für Ausdrucks Vorlagen – z `(valarray+valarray)` . b..

Um das **`auto`** Schlüsselwort zu verwenden, verwenden Sie es anstelle eines Typs, um eine Variable zu deklarieren, und geben Sie einen Initialisierungs Ausdruck an. Außerdem können Sie das **`auto`** -Schlüsselwort ändern, indem Sie Spezifizierer und Deklaratoren wie **`const`** , **`volatile`** , Pointer ( **`*`** ), Reference ( **`&`** ) und rvalue reference ( **`&&`** ) verwenden. Der Compiler wertet den Initialisierungsausdruck aus und verwendet dann diese Informationen, um den Typ der Variable herzuleiten.

Der Initialisierungs Ausdruck kann eine Zuweisung (Gleichheitszeichen Syntax), eine direkte Initialisierung (Funktionsformat Syntax), ein Ausdruck sein [`operator new`](new-operator-cpp.md) , oder der Initialisierungs Ausdruck kann der Parameter " *for-Range-Declaration* " in einer [Bereichs basierten `for` Anweisung (C++)](../cpp/range-based-for-statement-cpp.md) sein. Weitere Informationen finden Sie unter [Initialisierer](../cpp/initializers.md) und in den Codebeispielen weiter unten in diesem Dokument.

Das **`auto`** Schlüsselwort ist ein Platzhalter für einen Typ, aber es ist nicht selbst ein Typ. Daher kann das **`auto`** -Schlüsselwort nicht in Umwandlungen oder Operatoren wie und verwendet werden [`sizeof`](../cpp/sizeof-operator.md) (für C++/CLI) [`typeid`](../extensions/typeid-cpp-component-extensions.md) .

## <a name="usefulness"></a>Nützlichkeit

Das- **`auto`** Schlüsselwort ist eine einfache Möglichkeit zum Deklarieren einer Variablen, die einen komplizierten Typ aufweist. Beispielsweise können Sie verwenden, **`auto`** um eine Variable zu deklarieren, in der der Initialisierungs Ausdruck Vorlagen, Zeiger auf Funktionen oder Zeiger auf Member umfasst.

Sie können auch verwenden **`auto`** , um eine Variable in einem Lambda-Ausdruck zu deklarieren und zu initialisieren. Sie können den Typ der Variable nicht selbst deklarieren, da der Typ eines Lambdaausdrucks nur dem Compiler bekannt ist. Weitere Informationen finden Sie unter [Beispiele für Lambda-Ausdrücke](../cpp/examples-of-lambda-expressions.md).

## <a name="trailing-return-types"></a>Nachstehende Rückgabetypen

Sie können **`auto`** in Verbindung mit dem **`decltype`** Typspezifizierer verwenden, um Vorlagen Bibliotheken zu schreiben. Verwenden **`auto`** **`decltype`** Sie und, um eine Vorlagen Funktion zu deklarieren, deren Rückgabetyp von den Typen seiner Vorlagen Argumente abhängt. Oder verwenden **`auto`** Sie und, **`decltype`** um eine Vorlagen Funktion zu deklarieren, die einen Aufrufe einer anderen Funktion umschließt und dann den Rückgabetyp dieser anderen Funktion zurückgibt. Weitere Informationen finden Sie unter [`decltype`](../cpp/decltype-cpp.md).

## <a name="references-and-cv-qualifiers"></a>Verweise und CV-Qualifizierer

Beachten Sie, dass mithilfe von **`auto`** Drop Verweise, **`const`** Qualifizierer und **`volatile`** Qualifizierer Betrachten Sie das folgenden Beispiel:

```cpp
// cl.exe /analyze /EHsc /W4
#include <iostream>

using namespace std;

int main( )
{
    int count = 10;
    int& countRef = count;
    auto myAuto = countRef;

    countRef = 11;
    cout << count << " ";

    myAuto = 12;
    cout << count << endl;
}
```

Im vorherigen Beispiel ist myauto ein **`int`** und kein **`int`** Verweis, sodass die Ausgabe ist `11 11` , und nicht `11 12` wie wäre der Fall, wenn der Verweis Qualifizierer nicht von gelöscht wurde **`auto`** .

## <a name="type-deduction-with-braced-initializers-c14"></a>Typableitung mit geschweizten Initialisierern (c++ 14)

Im folgenden Codebeispiel wird gezeigt, wie eine Variable mit geschweiften Klammern initialisiert wird **`auto`** . Beachten Sie den Unterschied zwischen B und C sowie zwischen a und E.

```cpp
#include <initializer_list>

int main()
{
    // std::initializer_list<int>
    auto A = { 1, 2 };

    // std::initializer_list<int>
    auto B = { 3 };

    // int
    auto C{ 4 };

    // C3535: cannot deduce type for 'auto' from initializer list'
    auto D = { 5, 6.7 };

    // C3518 in a direct-list-initialization context the type for 'auto'
    // can only be deduced from a single initializer expression
    auto E{ 8, 9 };

    return 0;
}
```

## <a name="restrictions-and-error-messages"></a>Beschränkungen und Fehlermeldungen

In der folgenden Tabelle sind die Einschränkungen der Verwendung des **`auto`** -Schlüssel Worts und die entsprechende Diagnose Fehlermeldung aufgeführt, die der Compiler ausgibt.

|Fehlernummer|Beschreibung|
|------------------|-----------------|
|[C3530](../error-messages/compiler-errors-2/compiler-error-c3530.md)|Das **`auto`** Schlüsselwort kann nicht mit einem anderen Typspezifizierer kombiniert werden.|
|[C3531](../error-messages/compiler-errors-2/compiler-error-c3531.md)|Ein Symbol, das mit dem- **`auto`** Schlüsselwort deklariert wird, muss über einen Initialisierer verfügen.|
|[C3532](../error-messages/compiler-errors-2/compiler-error-c3532.md)|Sie haben das **`auto`** Schlüsselwort fälschlicherweise verwendet, um einen Typ zu deklarieren. Sie haben zum Beispiel einen Methodenrückgabetyp oder ein Array deklariert.|
|[C3533](../error-messages/compiler-errors-2/compiler-error-c3533.md), [C3539](../error-messages/compiler-errors-2/compiler-error-c3539.md)|Ein Parameter-oder Vorlagen Argument kann nicht mit dem- **`auto`** Schlüsselwort deklariert werden.|
|[C3535](../error-messages/compiler-errors-2/compiler-error-c3535.md)|Eine Methode oder ein Vorlagen Parameter kann nicht mit dem- **`auto`** Schlüsselwort deklariert werden.|
|[C3536](../error-messages/compiler-errors-2/compiler-error-c3536.md)|Ein Symbol kann erst verwendet werden, wenn es initialisiert wurde. In der Praxis bedeutet dies, dass eine Variable nicht verwendet werden kann, um sich selbst zu initialisieren.|
|[C3537](../error-messages/compiler-errors-2/compiler-error-c3537.md)|Sie können nicht in einen Typ umwandeln, der mit dem- **`auto`** Schlüsselwort deklariert wird.|
|[C3538](../error-messages/compiler-errors-2/compiler-error-c3538.md)|Alle Symbole in einer Deklaratorliste, die mit dem-Schlüsselwort deklariert wird, **`auto`** müssen in denselben Typ aufgelöst werden. Weitere Informationen finden Sie unter [Deklarationen und Definitionen](declarations-and-definitions-cpp.md).|
|[C3540](../error-messages/compiler-errors-2/compiler-error-c3540.md), [C3541](../error-messages/compiler-errors-2/compiler-error-c3541.md)|Die Operatoren [sizeof](../cpp/sizeof-operator.md) und [typeid](../extensions/typeid-cpp-component-extensions.md) können nicht auf ein Symbol angewendet werden, das mit dem- **`auto`** Schlüsselwort deklariert wird.|

## <a name="examples"></a>Beispiele

Diese Code Fragmente veranschaulichen einige Möglichkeiten, wie das- **`auto`** Schlüsselwort verwendet werden kann.

Die folgenden Deklarationen sind gleichwertig. In der ersten Anweisung wird die Variable als `j` Typ deklariert **`int`** . In der zweiten Anweisung `k` wird die Variable als Typ abgeleitet, **`int`** da der Initialisierungs Ausdruck (0) eine ganze Zahl ist.

```cpp
int j = 0;  // Variable j is explicitly type int.
auto k = 0; // Variable k is implicitly type int because 0 is an integer.
```

Die folgenden Deklarationen sind gleichwertig, die zweite Deklaration ist jedoch einfacher als die erste. Einer der überzeugendsten Gründe für die Verwendung des- **`auto`** Schlüssel Worts ist die Einfachheit.

```cpp
map<int,list<string>>::iterator i = m.begin();
auto i = m.begin();
```

Das folgende Code Fragment deklariert den Typ der Variablen `iter` und, `elem` Wenn die **`for`** -und-Bereichs **`for`** Schleifen beginnen.

```cpp
// cl /EHsc /nologo /W4
#include <deque>
using namespace std;

int main()
{
    deque<double> dqDoubleData(10, 0.1);

    for (auto iter = dqDoubleData.begin(); iter != dqDoubleData.end(); ++iter)
    { /* ... */ }

    // prefer range-for loops with the following information in mind
    // (this applies to any range-for with auto, not just deque)

    for (auto elem : dqDoubleData) // COPIES elements, not much better than the previous examples
    { /* ... */ }

    for (auto& elem : dqDoubleData) // observes and/or modifies elements IN-PLACE
    { /* ... */ }

    for (const auto& elem : dqDoubleData) // observes elements IN-PLACE
    { /* ... */ }
}
```

Das folgende Code Fragment verwendet die **`new`** Operator-und Zeiger Deklaration, um Zeiger zu deklarieren.

```cpp
double x = 12.34;
auto *y = new auto(x), **z = new auto(&x);
```

Im folgenden Codefragment werden mehrere Symbole in jeder Deklarationsanweisung deklariert. Beachten Sie, dass alle Symbole in jeder Anweisung in den gleichen Typ aufgelöst werden.

```cpp
auto x = 1, *y = &x, **z = &y; // Resolves to int.
auto a(2.01), *b (&a);         // Resolves to double.
auto c = 'a', *d(&c);          // Resolves to char.
auto m = 1, &n = m;            // Resolves to int.
```

Dieses Codefragment verwendet den bedingten Operator (`?:`), um die `x`-Variable als ganze Zahl mit einem Wert von 200 zu deklarieren:

```cpp
int v1 = 100, v2 = 200;
auto x = v1 > v2 ? v1 : v2;
```

Das folgende Code Fragment Initialisiert eine Variable `x` mit Type **`int`** , Variable `y` zu einem Verweis auf den Typ **`const int`** und Variable `fp` zu einem Zeiger auf eine Funktion, die den Typ zurückgibt **`int`** .

```cpp
int f(int x) { return x; }
int main()
{
    auto x = f(0);
    const auto& y = f(1);
    int (*p)(int x);
    p = f;
    auto fp = p;
    //...
}
```

## <a name="see-also"></a>Siehe auch

[`auto`Schlüsselwort](../cpp/auto-keyword.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`/Zc:auto`(Typ der deduce-Variable)](../build/reference/zc-auto-deduce-variable-type.md)<br/>
[`sizeof`KOM](../cpp/sizeof-operator.md)<br/>
[`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
[`operator new`](new-operator-cpp.md)<br/>
[Deklarationen und Definitionen](declarations-and-definitions-cpp.md)<br/>
[Beispiele für Lambda-Ausdrücke](../cpp/examples-of-lambda-expressions.md)<br/>
[Initialisierer](../cpp/initializers.md)<br/>
[`decltype`](../cpp/decltype-cpp.md)
