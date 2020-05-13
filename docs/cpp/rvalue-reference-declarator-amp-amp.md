---
title: Rvalue-Referenzdeklarator:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: 53729cca7c259bc2d3b792ddc3509d5fc3bd255a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749831"
---
# <a name="rvalue-reference-declarator-ampamp"></a>Rvalue-Referenzdeklarator:&amp;&amp;

Enthält einen Verweis auf einen rvalue-Ausdruck.

## <a name="syntax"></a>Syntax

```
type-id && cast-expression
```

## <a name="remarks"></a>Bemerkungen

Mit rvalue-Verweisen haben Sie die Möglichkeit, einen lvalue von einem rvalue zu unterscheiden. Lvalue-Verweise und rvalue-Verweise sind syntaktisch und semantisch ähnlich, folgen jedoch etwas unterschiedlichen Regeln. Weitere Informationen zu Lvalues und Rvalues finden Sie unter [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md). Weitere Informationen zu lvalue-Referenzen finden Sie unter [Lvalue Reference Declarator: &](../cpp/lvalue-reference-declarator-amp.md).

In den folgenden Abschnitten wird beschrieben, wie rvalue-Referenzen die Implementierung von *Bewegungssemantik* und *perfekter Weiterleitung*unterstützen.

## <a name="move-semantics"></a>Verschiebesemantik

Rvalue-Referenzen unterstützen die Implementierung von *Move-Semantik*, die die Leistung Ihrer Anwendungen erheblich steigern kann. Mithilfe der Verschiebesemantik können Sie Code schreiben, der Ressourcen (wie dynamisch zugeordneten Speicher) von einem Objekt zu einem anderen überträgt. Die Verschiebesemantik funktioniert, da sie das Übertragen von Ressourcen von temporären Objekten ermöglicht, auf die nicht an anderer Stelle im Programm verwiesen werden kann.

Um die Verschiebungssemantik zu implementieren, stellen Sie in der Regel einen *Verschiebungskonstruktor* und optional einen Verschiebungszuweisungsoperator (**operator=**) für Ihre Klasse bereit. Kopier- und Zuordnungsvorgänge, deren Quellen rvalues sind, nutzen dann automatisch die Verschiebesemantik. Im Gegensatz zum standardmäßigen Kopierkonstruktor stellt der Compiler keinen standardmäßigen Bewegungskonstruktor bereit. Weitere Informationen zum Schreiben eines Verschiebungskonstruktors und zur Verwendung in der Anwendung finden Sie unter Verschieben von [Konstruktoren und Verschieben von Zuweisungsoperatoren (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

Sie können auch gewöhnliche Funktionen und Operatoren überladen, um die Verschiebesemantik zu nutzen. Visual Studio 2010 führt die Bewegungssemantik in die C++-Standardbibliothek ein. Beispielsweise implementiert die `string`-Klasse Vorgänge, die Verschiebesemantik ausführen. Betrachten Sie das folgende Beispiel, in dem mehrere Zeichenfolgen verkettet werden und das Ergebnis ausgegeben wird:

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Vor Visual Studio 2010 weist jeder Aufruf von **Operator+** ein neues temporäres `string` Objekt (einen rvalue) zu und gibt es zurück. **operator+** kann keine Zeichenfolge an die andere anhängen, da nicht bekannt ist, ob es sich bei den Quellzeichenfolgen um lvalues oder rvalues handelt. Wenn die Quellzeichenfolgen beide lvalues sind, wird möglicherweise an anderer Stelle im Programm auf sie verwiesen, und sie dürfen deshalb nicht geändert werden. Mithilfe von rvalue-Referenzen kann **operator+** so geändert werden, dass rvalues genommen wird, auf die an anderer Stelle im Programm nicht verwiesen werden kann. Daher kann **operator+** jetzt eine Zeichenfolge an eine andere anhängen. Dadurch kann die Anzahl dynamischer Speicherbelegungen beträchtlich reduziert werden, die die `string`-Klasse ausführen muss. Weitere Informationen zur `string` Klasse finden Sie unter [basic_string Klasse](../standard-library/basic-string-class.md).

Die Verschiebesemantik ist auch hilfreich, wenn der Compiler keine Rückgabewertoptimierung (Return Value Optimization, RVO) oder benannte Rückgabewertoptimierung (Named Return Value Optimization, NRVO) verwenden kann. In diesen Fällen ruft der Compiler den Verschiebekonstruktor auf, wenn der Typ diesen definiert.

Das Beispiel zum Einfügen eines Elements in ein `vector`-Objekt hilft Ihnen, die Verschiebesemantik besser zu verstehen. Wenn die Kapazität des `vector`-Objekts überschritten wird, muss das `vector`-Objekt Speicher für seine Elemente neu zuteilen und dann jedes Element an einen anderen Speicherort kopieren, um für das eingefügte Element Platz zu schaffen. Wenn ein Einfügevorgang ein Element kopiert, wird ein neues Element erstellt, der Kopierkonstruktor aufgerufen, um die Daten aus dem vorherigen Element in das neue Element zu kopieren, und anschließend das vorherige Element zerstört. Mithilfe der Verschiebesemantik können Sie Objekte direkt verschieben, ohne speicherintensive Speicherbelegungs- und Kopiervorgänge ausführen zu müssen.

Um die Verschiebesemantik im `vector`-Beispiel zu nutzen, können Sie einen Bewegungskonstruktor schreiben, um Daten von einem Objekt in ein anderes zu verschieben.

Weitere Informationen zur Einführung der Verschiebungssemantik in die C++-Standardbibliothek in Visual Studio 2010 finden Sie unter [C++ Standardbibliothek](../standard-library/cpp-standard-library-reference.md).

## <a name="perfect-forwarding"></a>Perfekte Weiterleitung

Perfekte Weiterleitung reduziert die Notwendigkeit überladener Funktionen und hilft, das Weiterleitungsproblem zu vermeiden. Das *Weiterleitungsproblem* kann auftreten, wenn Sie eine generische Funktion schreiben, die Verweise als Parameter verwendet und diese Parameter an eine andere Funktion weiterleitet (oder *weiterleitet).* Wenn beispielsweise die generische Funktion einen Parameter vom Typ `const T&` akzeptiert, kann die aufgerufene Funktion den Wert dieses Parameters nicht ändern. Wenn die generische Funktion einen Parameter vom Typ `T&` akzeptiert, dann kann die Funktion nicht mithilfe eines rvalue (z. B. eines temporären Objekts oder Ganzzahlliterals) aufgerufen werden.

Um dieses Problem zu lösen, müssen Sie normalerweise überladene Versionen der generischen Funktion bereitstellen, die sowohl `T&` als auch `const T&` für jeden ihrer Parameter akzeptieren. Dadurch erhöht sich die Anzahl von überladenen Funktionen exponentiell mit der Anzahl von Parametern. Mit rvalue-Verweisen können Sie eine Version einer Funktion schreiben, die beliebige Argumente akzeptiert und diese an eine andere Funktion weiterleitet, als wäre die andere Funktion direkt aufgerufen worden.

Betrachten Sie das folgende Beispiel, in dem vier Typen, `W`, `X`, `Y` und `Z`, deklariert werden. Der Konstruktor für jeden Typ verwendet eine andere Kombination aus **const-** und non-const-lvalue-Referenzen als Parameter.**const**

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

Angenommen, Sie möchten eine generische Funktion schreiben, die Objekte generiert. Im folgenden Beispiel wird eine Möglichkeit zum Schreiben dieser Funktion dargestellt:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

Im folgenden Beispiel wird ein gültiger Aufruf der `factory`-Funktion veranschaulicht:

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

Das folgende Beispiel enthält jedoch keinen gültigen Aufruf der `factory`-Funktion, da `factory` lvalue-Verweise akzeptiert, die als Parameter änderbar sind, sie wird jedoch mithilfe von rvalues aufgerufen:

```cpp
Z* pz = factory<Z>(2, 2);
```

Um dieses Problem zu lösen, müssen Sie normalerweise eine überladene Version der `factory`-Funktion für jede Kombination von `A&`- und `const A&`-Parametern erstellen. Mit rvalue-Verweisen können Sie eine Version der `factory`-Funktion schreiben, wie im folgenden Beispiel gezeigt:

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

In diesem Beispiel werden rvalue-Verweise als Parameter für die `factory`-Funktion verwendet. Der Zweck der [funktion::forward](../standard-library/utility-functions.md#forward) besteht darin, die Parameter der Factory-Funktion an den Konstruktor der Vorlagenklasse weiterzuleiten.

Das folgende Beispiel zeigt die `main`-Funktion, die die überarbeitete `factory`-Funktion verwendet, um Instanzen der Klassen `W`, `X`, `Y` und `Z` zu erstellen. Die überarbeitete `factory`-Funktion leitet ihre Parameter (entweder lvalues oder rvalues) an den entsprechenden Klassenkonstruktor weiter.

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>Zusätzliche Eigenschaften von rvalue-Verweisen

**Sie können eine Funktion überladen, damit ein lvalue-Verweis und ein rvalue-Verweis akzeptiert werden.**

Durch Überladen einer Funktion, um einen const-lvalue-Verweis oder einen rvalue-Verweis zu übernehmen, können Sie Code schreiben, der zwischen nicht veränderbaren Objekten (lwerten) und veränderbaren temporären Werten (rvalues) unterscheidet. **const** Sie können ein Objekt an eine Funktion übergeben, die einen rvalue-Verweis annimmt, es sei denn, das Objekt ist als **const**markiert. Das folgende Beispiel zeigt die `f`-Funktion, die überladen ist, damit ein lvalue-Verweis und ein rvalue-Verweis akzeptiert wird. Die `main`-Funktion ruft `f` sowohl mit lvalue als auch mit rvalue auf.

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

In diesem Beispiel übergibt der erste Aufruf von `f` eine lokale Variable (lvalue) als Argument. Der zweite Aufruf von `f` übergibt ein temporäres Objekt als Argument. Da auf das temporäre Objekt nicht an anderer Stelle im Programm verwiesen werden kann, stellt der Aufruf eine Bindung an die überladene Version von `f` her, die einen rvalue-Verweis akzeptiert, der das Objekt ändern kann.

**Der Compiler behandelt einen benannten rvalue-Verweis als lvalue und einen unbenannten rvalue-Verweis als rvalue.**

Wenn Sie eine Funktion schreiben, die einen rvalue-Verweis als Parameter akzeptiert, wird dieser Parameter im Text der Funktion als lvalue behandelt. Der Compiler behandelt einen benannten rvalue-Verweis als lvalue, da auf ein benanntes Objekt von mehreren Teilen eines Programms verwiesen werden kann. Es wäre gefährlich, zuzulassen, dass mehrere Teile eines Programms Ressourcen von diesem Objekt ändern oder entfernen. Wenn beispielsweise mehrere Teile eines Programms versuchen, Ressourcen vom gleichen Objekt zu übertragen, wird nur der erste Teil die Ressource erfolgreich übertragen.

Das folgende Beispiel zeigt die `g`-Funktion, die überladen ist, damit ein lvalue-Verweis und ein rvalue-Verweis akzeptiert wird. Die `f`-Funktion akzeptiert einen rvalue-Verweis als ihren Parameter (einen benannten rvalue-Verweis) und gibt einen rvalue-Verweis (einen unbenannten rvalue-Verweis) zurück. Im Aufruf von `g` von `f` wählt die Überladungsauflösung die Version von `g` aus, die einen lvalue-Verweis akzeptiert, da der Text von `f` den Parameter als lvalue behandelt. Im Aufruf von `g` von `main` wählt die Überladungsauflösung die Version von `g` aus, die einen rvalue-Verweis akzeptiert, da `f` einen rvalue-Verweis zurückgibt.

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

Dieses Beispiel erzeugt die folgende Ausgabe:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

In diesem Beispiel übergibt die `main`-Funktion einen rvalue an `f`. Der Text von `f` behandelt den benannten Parameter als lvalue. Der Aufruf von `f` zu `g` bindet den Parameter an einen lvalue-Verweis (die erste überladene Version von `g`).

- **Sie können ein lvalue-Verweis in einen rvalue-Verweis umwandeln.**

Mit der Funktion C++ Standard library [std::move](../standard-library/utility-functions.md#move) können Sie ein Objekt in einen rvalue-Verweis auf dieses Objekt konvertieren. Alternativ können Sie das **Schlüsselwort static_cast** verwenden, um einen lvalue in einen rvalue-Verweis umzuwerfen, wie im folgenden Beispiel gezeigt:

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

Dieses Beispiel erzeugt die folgende Ausgabe:

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**Funktionsvorlagen leiten ihre Vorlagenargumenttypen ab und verwenden dann Verweisreduzierungsregeln.**

Es ist üblich, eine Funktionsvorlage zu schreiben, die ihre Parameter an eine andere Funktion übergibt (oder *weiterleitet).* Es ist wichtig zu wissen, wie die Ableitung des Vorlagentyps für Funktionsvorlagen, die rvalue-Verweise akzeptieren, funktioniert.

Wenn das Funktionsargument ein rvalue ist, geht der Compiler davon aus, dass das Argument ein rvalue-Verweis ist. Wenn Sie beispielsweise einen rvalue-Verweis auf ein Objekt vom Typ `X` an eine Vorlagenfunktion übergeben, die Typ `T&&` als Parameter akzeptiert, geht die Vorlagenargumentableitung davon aus, dass `T``X` sein muss. Daher weist der Parameter den Typ `X&&` auf. Wenn das Funktionsargument ein lvalue oder **const** lvalue ist, leitet der Compiler seinen Typ als lvalue-Referenz oder **const** lvalue-Referenz dieses Typs ab.

Im folgenden Beispiel wird eine Strukturvorlage deklariert und dann für verschiedene Verweistypen spezialisiert. Die `print_type_and_value`-Funktion akzeptiert einen rvalue-Verweis als Parameter und leitet ihn an die entsprechende spezialisierte Version der `S::print`-Methode weiter. Die `main`-Funktion zeigt die verschiedenen Möglichkeiten, die `S::print`-Methode aufzurufen.

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

Dieses Beispiel erzeugt die folgende Ausgabe:

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

Um die einzelnen Aufrufe der `print_type_and_value`-Funktion aufzulösen, führt der Compiler zunächst eine Ableitung der Vorlagenargumente aus. Der Compiler verwendet dann die Verweisreduzierungsregeln, wenn er die abgeleiteten Vorlagenargumente für die Parametertypen ersetzt. Zum Beispiel führt die Übergabe der lokalen Variable `s1` an die `print_type_and_value`-Funktion dazu, dass der Compiler die folgende Funktionssignatur erstellt:

```cpp
print_type_and_value<string&>(string& && t)
```

Der Compiler verwendet Verweisreduzierungsregeln, um die Signatur folgendermaßen zu reduzieren:

```cpp
print_type_and_value<string&>(string& t)
```

Diese Version der `print_type_and_value`-Funktion leitet dann den Parameter an die richtige spezialisierte Version der `S::print`-Methode weiter.

Die folgende Tabelle fasst die Verweisreduzierungsregeln für die Ableitung des Vorlagenargumenttyps zusammen:

|||
|-|-|
|Erweiterter Typ|Reduzierter Typ|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

Vorlagenargumentableitung ist ein wichtiger Bestandteil der Implementierung der perfekten Weiterleitung. Der Abschnitt zur perfekten Weiterleitung, die bereits besprochen wurde, beschreibt die perfekte Weiterleitung im Detail.

## <a name="summary"></a>Zusammenfassung

Rvalue-Verweise unterscheiden lvalues von rvalues. Sie können Ihnen helfen, die Leistung der Anwendungen zu verbessern, indem die Notwendigkeit unnötiger Speicherbelegungs- und Kopiervorgänge beseitigt wird. Sie können damit auch eine Version einer Funktion schreiben, die beliebige Argumente akzeptiert und diese an eine andere Funktion weiterleitet, als wäre die andere Funktion direkt aufgerufen worden.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Lvalue-Verweisdeklarator: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Bewegungskonstruktoren und Bewegungszuweisungsoperatoren (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)
