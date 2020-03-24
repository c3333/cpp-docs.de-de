---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180211"
---
# <a name="decltype--c"></a>decltype (C++)

Der **decltype** -Typspezifizierer gibt den Typ eines angegebenen Ausdrucks aus. Der **decltype** -Typspezifizierer ist in erster Linie für Entwickler [nützlich, die](../cpp/auto-cpp.md)Vorlagen Bibliotheken schreiben. Verwenden Sie **Auto** und **decltype** , um eine Vorlagen Funktion zu deklarieren, deren Rückgabetyp von den Typen seiner Vorlagen Argumente abhängt. Oder verwenden Sie **Auto** und **decltype** , um eine Vorlagen Funktion zu deklarieren, die einen Aufrufe einer anderen Funktion umschließt und anschließend den Rückgabetyp der umschachtelten Funktion zurückgibt.

## <a name="syntax"></a>Syntax

```
decltype( expression )
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*expression*|Ein Ausdruck. Weitere Informationen finden Sie unter [Ausdrücke](../cpp/expressions-cpp.md).|

## <a name="return-value"></a>Rückgabewert

Der Typ des *Ausdrucks* Parameters.

## <a name="remarks"></a>Bemerkungen

Der **decltype** -Typspezifizierer wird in Visual Studio 2010 oder höheren Versionen unterstützt und kann mit System eigenem oder verwaltetem Code verwendet werden. `decltype(auto)` (C++14) wird in Visual Studio 2015 und höher unterstützt.

Der Compiler verwendet die folgenden Regeln, um den Typ des *Ausdrucks* Parameters zu bestimmen.

- Wenn der *Expression* -Parameter ein Bezeichner oder ein [Klassenmember-Zugriff](../cpp/member-access-operators-dot-and.md)ist, ist `decltype(expression)` der Typ der Entität, benannt nach *Ausdruck*. Wenn keine solche Entität vorhanden ist oder der *Ausdrucks* Parameter einen Satz überladener Funktionen benennt, gibt der Compiler eine Fehlermeldung aus.

- Wenn der *Expression* -Parameter ein Aufrufen einer Funktion oder einer überladenen Operator Funktion ist, ist `decltype(expression)` der Rückgabetyp der Funktion. Klammern um einen überladenen Operator werden ignoriert.

- Wenn der *Expression* -Parameter ein [Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)ist, ist `decltype(expression)` der Typ des *Ausdrucks*. Wenn der *Expression* -Parameter ein [Lvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)ist, ist `decltype(expression)` ein [Lvalue-Verweis](../cpp/lvalue-reference-declarator-amp.md) auf den Typ des *Ausdrucks*.

Im folgenden Codebeispiel werden einige Verwendungen des **decltype** -Typspezifizierers veranschaulicht. Angenommen, Sie haben die folgenden Anweisungen codiert.

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

Überprüfen Sie als nächstes die Typen, die von den vier **decltype** -Anweisungen in der folgenden Tabelle zurückgegeben werden.

|-Anweisung.|type|Notizen|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|Ein [rvalue-Verweis](../cpp/rvalue-reference-declarator-amp-amp.md) auf einen **Konstanten int**.|
|`decltype(var);`|**int**|Der Typ der `var`-Variablen.|
|`decltype(a->x);`|**double**|Der Typ des Memberzugriffs.|
|`decltype((a->x));`|`const double&`|Die innere Klammer bewirkt, dass die Anweisung als Ausdruck anstatt als Memberzugriff ausgewertet wird. Und da `a` als `const` Zeiger deklariert ist, ist der Typ ein Verweis auf den **Konstanten Double**-Wert.|

## <a name="decltype-and-auto"></a>"decltype" und "auto"

In c++ 14 können Sie `decltype(auto)` ohne nachfolgenden Rückgabetyp verwenden, um eine Vorlagen Funktion zu deklarieren, deren Rückgabetyp von den Typen seiner Vorlagen Argumente abhängt.

In c++ 11 können Sie den **decltype** -Typspezifizierer für einen nachfolgenden Rückgabetyp sowie das **Auto** -Schlüsselwort verwenden, um eine Vorlagen Funktion zu deklarieren, deren Rückgabetyp von den Typen der zugehörigen Vorlagen Argumente abhängt. Betrachten Sie das folgende Codebeispiel, in dem der Rückgabetyp der Vorlagenfunktion von den Typen der Vorlagenargumente abhängt. Im Codebeispiel gibt der *unbekannte* Platzhalter an, dass der Rückgabetyp nicht angegeben werden kann.

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

Die Einführung des Typspezifizierers **decltype** ermöglicht einem Entwickler das Abrufen des Typs des Ausdrucks, den die Vorlagen Funktion zurückgibt. Verwenden Sie die *Alternative Funktions Deklarations Syntax* , die später angezeigt wird, das **Auto** -Schlüsselwort und den **decltype** -Typspezifizierer, um einen *spät angegebenen* Rückgabetyp zu deklarieren. Der spät angegebene Rückgabetyp wird bestimmt, wenn die Deklaration kompiliert wird, anstatt wenn sie codiert wird.

Der folgende Prototyp veranschaulicht die Syntax einer alternativen Funktionsdeklaration. Beachten Sie, dass die **Konstanten** and **volatile** -Qualifizierer und die **throw** [Exception-Spezifikation](../cpp/exception-specifications-throw-cpp.md) optional sind. Der *function_body* -Platzhalter stellt eine Verbund Anweisung dar, die die Funktionsweise der Funktion angibt. Als bewährte Programmier Übung sollte der *Ausdrucks* Platzhalter in der **decltype** -Anweisung mit dem von der **Return** -Anweisung angegebenen Ausdruck in der *function_body*identisch sein.

**Auto** *function_name* **(** *Parameters*<sub>opt</sub> **)** **Konstanten**<sub>opt</sub> **volatile**<sub>opt</sub> **->** **decltype (** *Ausdruck* **)** **throw**<sub>opt</sub> **{** *function_body* **};**

Im folgenden Codebeispiel wird der spät angegebene Rückgabetyp der `myFunc`-Vorlagenfunktion von den Typen der `t`- und `u`-Vorlagenargumente bestimmt. Als bewährte Programmier Übung verwendet das Codebeispiel auch Rvalue-Verweise und die `forward` Funktions Vorlage, die eine *perfekte Weiterleitung*unterstützen. Weitere Informationen finden Sie unter [RValue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>„decltyp“ und Weiterleitungsfunktionen (C++11)

Weiterleitungsfunktionen umschließen Aufrufe von anderen Funktionen. Denken Sie an eine Funktionsvorlage, die ihre Argumente oder die Ergebnisse eines Ausdrucks, der diese Argumente beinhaltet, an eine andere Funktion weiterleitet. Darüber hinaus gibt die Weiterleitungsfunktion das Ergebnis des Aufrufs der anderen Funktion zurück. In diesem Szenario muss der Rückgabetyp der Weiterleitungsfunktion mit dem Rückgabetyp der umschlossenen Funktion identisch sein.

In diesem Szenario können Sie keinen geeigneten Typausdruck ohne den **decltype** -Typspezifizierer schreiben. Der **decltype** -Typspezifizierer ermöglicht generische Weiterleitungs Funktionen, da er erforderliche Informationen darüber nicht verliert, ob eine Funktion einen Verweistyp zurückgibt. Ein Codebeispiel für eine Weiterleitungsfunktion finden Sie im vorherigen `myFunc`-Vorlagenfunktionsbeispiel.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird der spät angegebene Rückgabetyp der `Plus()`-Vorlagenfunktion deklariert. Die `Plus`-Funktion verarbeitet die beiden Operanden mit dem **Operator +** Overload. Demzufolge hängen die Interpretation des Plus-Operators (+) und der Rückgabetyp der `Plus`-Funktion von den Typen der Funktionsargumente ab.

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>Beispiel

**Visual Studio 2017 und höher:** Der Compiler analysiert decltype-Argumente, wenn die Vorlagen deklariert und nicht instanziiert werden. Wenn eine unabhängige Spezialisierung im decltype-Argument gefunden wird, wird sie nicht zum Zeitpunkt der Instanziierung zurückgestellt werden. Sie wird sofort verarbeitet, und alle resultierenden Fehler können zu diesem Zeitpunkt untersucht werden.

Das folgende Beispiel zeigt einen solchen Compilerfehler, der zum Zeitpunkt der Deklaration ausgelöst wird:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Requirements (Anforderungen)

Visual Studio 2010 oder höhere Versionen.

`decltype(auto)` erfordert Visual Studio 2015 oder höher.
