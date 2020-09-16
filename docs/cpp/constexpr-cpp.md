---
title: constexpr (C++)
description: Leitfaden zum C++-Programmiersprachen constexpr Schlüsselwort.
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 57ebf4bf69c768bfcd2e4d26a5c3334ca788b08f
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569553"
---
# <a name="no-locconstexpr-c"></a>constexpr (C++)

Das Schlüsselwort **`constexpr`** wurde in c++ 11 eingeführt und in c++ 14 verbessert. Es bedeutet * const Ant-Ausdruck*. Ebenso **`const`** kann Sie auf Variablen angewendet werden: ein Compilerfehler wird ausgelöst, wenn von einem Code versucht wird, den Wert von "y" zu mod if . Im Gegensatz zu **`const`** **`constexpr`** kann auch auf Funktionen und klassenruktoren angewendet werden const . **`constexpr`** Gibt an, dass der Wert oder der Rückgabewert const Ant ist und, sofern möglich, zur Kompilierzeit berechnet wird.

Ein **`constexpr`** ganzzahliger Wert kann überall dort verwendet werden, wo eine const Ganzzahl erforderlich ist, beispielsweise in Vorlagen Argumenten und Array Deklarationen. Wenn ein Wert zur Kompilierzeit anstelle der Laufzeit berechnet wird, hilft er dem Programm, schneller auszuführen und weniger Arbeitsspeicher zu verwenden.

Um die Komplexität der Kompilierzeit- const Ant-Berechnungen und Ihre potenziellen Auswirkungen auf die Kompilierungszeit einzuschränken, erfordert der c++ 14-Standard, dass die Typen in const Ant-Ausdrücken [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types)sind.

## <a name="syntax"></a>Syntax

> **`constexpr`***Literaltyp* *Ident if Ier* **=** * const Ant-Expression* **;**\
> **`constexpr`***Literaltyp* *Ident if Ier* **{** * const Ant-Expression* **}** **;**\
> **`constexpr`***Literaltyp* *Ident if Ier* **(** *para* Metern **)** **;**\
> **`constexpr`***ctor* **(** *parametriams* **)** **;**

## <a name="parameters"></a>Parameter

*params*\
Ein oder mehrere Parameter, von denen jeder ein Literaltyp sein muss und selbst ein Ant-Ausdruck sein muss const .

## <a name="return-value"></a>Rückgabewert

Eine **`constexpr`** Variable oder Funktion muss einen [Literaltyp](trivial-standard-layout-and-pod-types.md#literal_types)zurückgeben.

## <a name="no-locconstexpr-variables"></a>constexpr-Variablen

Die primäre d-unter if Bezugnahme zwischen den **`const`** **`constexpr`** Variablen und besteht darin, dass die Initialisierung einer **`const`** Variablen bis zur Laufzeit verzögert werden kann. Eine **`constexpr`** Variable muss zum Zeitpunkt der Kompilierung initialisiert werden.  Alle **`constexpr`** Variablen sind **`const`** .

- Eine Variable kann mit deklariert werden **`constexpr`** , wenn Sie einen Literaltyp aufweist und initialisiert wird. Wenn die Initialisierung for durch einen ruktor pro Med erfolgt const , const muss der ruktor als deklariert werden **`constexpr`** .

- Ein Verweis kann als deklariert werden **`constexpr`** , wenn beide Bedingungen erfüllt sind: das Objekt, auf das verwiesen wird, wird von einem const Ant-Ausdruck initialisiert, und alle während der Initialisierung aufgerufenen impliziten Konvertierungen sind ebenfalls const Ant-Ausdrücke.

- Alle Deklarationen einer **`constexpr`** Variablen oder Funktion müssen über die **`constexpr`** Spezifikationen "Ier" verfügen if .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="no-locconstexpr-functions"></a><a name="constexpr_functions"></a> constexpr-Funktionen

Eine **`constexpr`** Funktion ist eine Funktion, deren Rückgabewert zur Kompilierzeit zur Kompilierzeit zu verarbeiten ist, wenn Sie den Code benötigt. Zum Verarbeiten von Code ist der Rückgabewert zur Kompilierzeit erforderlich, um eine Variable zu initialisieren **`constexpr`** , oder um ein Nichttyp-Vorlagen Argument bereitzustellen. Wenn die Argumente **`constexpr`** Werte sind, **`constexpr`** erzeugt eine Funktion eine Kompilierzeit const Ant. Wenn Sie mit nicht-- **`constexpr`** Argumenten aufgerufen werden oder wenn der Wert zur Kompilierzeit nicht erforderlich ist, wird zur Laufzeit ein Wert erzeugt, wie eine reguläre Funktion. (Dieses duale Verhalten speichert Sie, weil Sie **`constexpr`** nicht mehr als eine- **`constexpr`** Version derselben Funktion schreiben müssen.)

Eine **`constexpr`** Funktion oder eine const ructor ist implizit **`inline`** .

Die folgenden Regeln gelten für constexpr Funktionen:

- Eine **`constexpr`** Funktion muss nur [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types)akzeptieren und zurückgeben.

- Eine **`constexpr`** Funktion kann rekursiv sein.

- Sie kann nicht [virtuell](../cpp/virtual-cpp.md)sein. Ein const ruktor kann nicht definiert werden, **`constexpr`** Wenn die einschließende Klasse über virtuelle Basisklassen verfügt.

- Der Text kann als `= default` oder `= delete` definiert werden.

- Der Text kann keine- **`goto`** Anweisungen oder- **`try`** Blöcke enthalten.

- Eine explizite Spezialisierung einer nicht-- **`constexpr`** Vorlage kann wie folgt deklariert werden **`constexpr`** :

- Eine explizite Spezialisierung einer **`constexpr`** Vorlage muss nicht auch wie folgt lauten **`constexpr`** :

Die folgenden Regeln gelten für **`constexpr`** Funktionen in Visual Studio 2017 und höher:

- Sie enthält möglicherweise die **`if`** -und **`switch`** -Anweisungen sowie alle Schleifen Anweisungen, einschließlich **`for`** , Bereichs basiertes **`for`** , **`while`** , und **do- while **.

- Sie kann lokale Variablen Deklarationen enthalten, aber die Variable muss initialisiert werden. Dabei muss es sich um einen Literaltyp handeln, der nicht **`static`** oder Thread lokal sein darf. Die lokal deklarierte Variable muss nicht sein **`const`** und kann geändert werden.

- Eine **`constexpr`** nicht- **`static`** Member-Funktion muss implizit sein **`const`** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}
```

> [!TIP]
> Beim Debuggen eines nicht optimierten Debugbuilds können Sie im Visual Studio-Debugger erkennen, ob eine **`constexpr`** Funktion zum Zeitpunkt der Kompilierung ausgewertet wird, indem Sie einen Haltepunkt einfügen. Wenn der Haltepunkt erreicht wird, wurde die Funktion zur Laufzeit aufgerufen.  Wenn dies nicht der Fall ist, wurde die Funktion zum Zeitpunkt der Kompilierung aufgerufen.

## <a name="extern-no-locconstexpr"></a>Extern constexpr

Die [/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) -Compileroption bewirkt, dass der Compiler [externe Verknüpfungen](../c-language/external-linkage.md) auf Variablen anwendet, die mit **extern constexpr **deklariert werden. In früheren Versionen von Visual Studio wendet Visual Studio standardmäßig entweder standardmäßig oder wenn **/Zc: externconstexpr-** die Spezifikation ist if , eine interne Verknüpfung auf Variablen an, **`constexpr`** auch wenn das **`extern`** Schlüsselwort verwendet wird. Die Option **/Zc: externconstexpr** ist ab Visual Studio 2017 Update 15,6 verfügbar und ist standardmäßig deaktiviert. Die [/permissive-](../build/reference/permissive-standards-conformance.md) -Option aktiviert **/Zc: externconstexpr**nicht.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt **`constexpr`** Variablen, Funktionen und einen benutzerdefinierten Typ. In der letzten Anweisung in `main()` ist die **`constexpr`** Member-Funktion `GetValue()` ein Lauf Zeit Aufruf, da der Wert zur Kompilierzeit nicht bekannt sein muss.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
}

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Anforderungen

Visual Studio 2015 oder höher.

## <a name="see-also"></a>Siehe auch

[Deklarationen und Definitionen](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
