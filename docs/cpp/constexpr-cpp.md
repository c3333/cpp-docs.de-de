---
title: ':::no-loc(constexpr)::: (C++)'
description: 'Leitfaden zum C++-Programmiersprachen :::no-loc(constexpr)::: Schlüsselwort.'
ms.date: 01/28/2020
f1_keywords:
- :::no-loc(constexpr):::_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- ':::no-loc(constexpr):::'
- ':::no-loc(const):::'
- ':::no-loc(inline):::'
- ':::no-loc(goto):::'
- ':::no-loc(try):::'
- ':::no-loc(if):::'
- ':::no-loc(switch):::'
- ':::no-loc(for):::'
- ':::no-loc(while):::'
ms.openlocfilehash: d66dc333b7ac9fba94221dc4efa723c7919ef88f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229024"
---
# <a name="no-locconstexpr-c"></a>:::no-loc(constexpr)::: (C++)

Das Schlüsselwort **`:::no-loc(constexpr):::`** wurde in c++ 11 eingeführt und in c++ 14 verbessert. Es bedeutet * :::no-loc(const)::: Ant-Ausdruck*. Ebenso **`:::no-loc(const):::`** kann Sie auf Variablen angewendet werden: ein Compilerfehler wird ausgelöst, wenn von einem Code versucht wird, den Wert von "y" zu mod :::no-loc(if)::: . Im Gegensatz zu **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** kann auch auf Funktionen und klassenruktoren angewendet werden :::no-loc(const)::: . **`:::no-loc(constexpr):::`** Gibt an, dass der Wert oder der Rückgabewert :::no-loc(const)::: Ant ist und, sofern möglich, zur Kompilierzeit berechnet wird.

Ein **`:::no-loc(constexpr):::`** ganzzahliger Wert kann überall dort verwendet werden, wo eine :::no-loc(const)::: Ganzzahl erforderlich ist, beispielsweise in Vorlagen Argumenten und Array Deklarationen. Wenn ein Wert zur Kompilierzeit anstelle der Laufzeit berechnet wird, hilft er dem Programm, schneller auszuführen und weniger Arbeitsspeicher zu verwenden.

Um die Komplexität der Kompilierzeit- :::no-loc(const)::: Ant-Berechnungen und Ihre potenziellen Auswirkungen auf die Kompilierungszeit einzuschränken, erfordert der c++ 14-Standard, dass die Typen in :::no-loc(const)::: Ant-Ausdrücken [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types)sind.

## <a name="syntax"></a>Syntax

> **`:::no-loc(constexpr):::`***Literaltyp* *Ident :::no-loc(if)::: Ier* **=** * :::no-loc(const)::: Ant-Expression* **;**\
> **`:::no-loc(constexpr):::`***Literaltyp* *Ident :::no-loc(if)::: Ier* **{** * :::no-loc(const)::: Ant-Expression* **}** **;**\
> **`:::no-loc(constexpr):::`***Literaltyp* *Ident :::no-loc(if)::: Ier* **(** *para* Metern **)** **;**\
> **`:::no-loc(constexpr):::`***ctor* **(** *parametriams* **)** **;**

## <a name="parameters"></a>Parameter

*params*\
Ein oder mehrere Parameter, von denen jeder ein Literaltyp sein muss und selbst ein Ant-Ausdruck sein muss :::no-loc(const)::: .

## <a name="return-value"></a>Rückgabewert

Eine **`:::no-loc(constexpr):::`** Variable oder Funktion muss einen [Literaltyp](trivial-standard-layout-and-pod-types.md#literal_types)zurückgeben.

## <a name="no-locconstexpr-variables"></a>:::no-loc(constexpr):::-Variablen

Die primäre d-unter :::no-loc(if)::: Bezugnahme zwischen den **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** Variablen und besteht darin, dass die Initialisierung einer **`:::no-loc(const):::`** Variablen bis zur Laufzeit verzögert werden kann. Eine **`:::no-loc(constexpr):::`** Variable muss zum Zeitpunkt der Kompilierung initialisiert werden.  Alle **`:::no-loc(constexpr):::`** Variablen sind **`:::no-loc(const):::`** .

- Eine Variable kann mit deklariert werden **`:::no-loc(constexpr):::`** , wenn Sie einen Literaltyp aufweist und initialisiert wird. Wenn die Initialisierung :::no-loc(for)::: durch einen ruktor pro Med erfolgt :::no-loc(const)::: , :::no-loc(const)::: muss der ruktor als deklariert werden **`:::no-loc(constexpr):::`** .

- Ein Verweis kann als deklariert werden **`:::no-loc(constexpr):::`** , wenn beide Bedingungen erfüllt sind: das Objekt, auf das verwiesen wird, wird von einem :::no-loc(const)::: Ant-Ausdruck initialisiert, und alle während der Initialisierung aufgerufenen impliziten Konvertierungen sind ebenfalls :::no-loc(const)::: Ant-Ausdrücke.

- Alle Deklarationen einer **`:::no-loc(constexpr):::`** Variablen oder Funktion müssen über die **`:::no-loc(constexpr):::`** Spezifikationen "Ier" verfügen :::no-loc(if)::: .

```cpp
:::no-loc(constexpr)::: float x = 42.0;
:::no-loc(constexpr)::: float y{108};
:::no-loc(constexpr)::: float z = exp(5, 3);
:::no-loc(constexpr)::: int i; // Error! Not initialized
int j = 0;
:::no-loc(constexpr)::: int k = j + 1; //Error! j not a :::no-loc(const):::ant expression
```

## <a name="no-locconstexpr-functions"></a><a name=":::no-loc(constexpr):::_functions"></a>:::no-loc(constexpr):::Funktionen

Eine **`:::no-loc(constexpr):::`** Funktion ist eine Funktion, deren Rückgabewert zur Kompilierzeit zur Kompilierzeit zu verarbeiten ist, wenn Sie den Code benötigt. Zum Verarbeiten von Code ist der Rückgabewert zur Kompilierzeit erforderlich, um eine Variable zu initialisieren **`:::no-loc(constexpr):::`** , oder um ein Nichttyp-Vorlagen Argument bereitzustellen. Wenn die Argumente **`:::no-loc(constexpr):::`** Werte sind, **`:::no-loc(constexpr):::`** erzeugt eine Funktion eine Kompilierzeit :::no-loc(const)::: Ant. Wenn Sie mit nicht-- **`:::no-loc(constexpr):::`** Argumenten aufgerufen werden oder wenn der Wert zur Kompilierzeit nicht erforderlich ist, wird zur Laufzeit ein Wert erzeugt, wie eine reguläre Funktion. (Dieses duale Verhalten speichert Sie, weil Sie **`:::no-loc(constexpr):::`** nicht mehr als eine- **`:::no-loc(constexpr):::`** Version derselben Funktion schreiben müssen.)

Eine **`:::no-loc(constexpr):::`** Funktion oder eine :::no-loc(const)::: ructor ist implizit **`:::no-loc(inline):::`** .

Die folgenden Regeln gelten für :::no-loc(constexpr)::: Funktionen:

- Eine **`:::no-loc(constexpr):::`** Funktion muss nur [Literaltypen](trivial-standard-layout-and-pod-types.md#literal_types)akzeptieren und zurückgeben.

- Eine **`:::no-loc(constexpr):::`** Funktion kann rekursiv sein.

- Sie kann nicht [virtuell](../cpp/virtual-cpp.md)sein. Ein :::no-loc(const)::: ruktor kann nicht definiert werden, **`:::no-loc(constexpr):::`** Wenn die einschließende Klasse über virtuelle Basisklassen verfügt.

- Der Text kann als `= default` oder `= delete` definiert werden.

- Der Text kann keine- **`:::no-loc(goto):::`** Anweisungen oder- **`:::no-loc(try):::`** Blöcke enthalten.

- Eine explizite Spezialisierung einer nicht-- **`:::no-loc(constexpr):::`** Vorlage kann wie folgt deklariert werden **`:::no-loc(constexpr):::`** :

- Eine explizite Spezialisierung einer **`:::no-loc(constexpr):::`** Vorlage muss nicht auch wie folgt lauten **`:::no-loc(constexpr):::`** :

Die folgenden Regeln gelten für **`:::no-loc(constexpr):::`** Funktionen in Visual Studio 2017 und höher:

- Sie enthält möglicherweise die **`:::no-loc(if):::`** -und **`:::no-loc(switch):::`** -Anweisungen sowie alle Schleifen Anweisungen, einschließlich **`:::no-loc(for):::`** , Bereichs basiertes **`:::no-loc(for):::`** , **`:::no-loc(while):::`** , und **do- :::no-loc(while)::: **.

- Sie kann lokale Variablen Deklarationen enthalten, aber die Variable muss initialisiert werden. Dabei muss es sich um einen Literaltyp handeln, der nicht **`static`** oder Thread lokal sein darf. Die lokal deklarierte Variable muss nicht sein **`:::no-loc(const):::`** und kann geändert werden.

- Eine **`:::no-loc(constexpr):::`** nicht- **`static`** Member-Funktion muss implizit sein **`:::no-loc(const):::`** .

```cpp
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Beim Debuggen eines nicht optimierten Debugbuilds können Sie im Visual Studio-Debugger erkennen, ob eine **`:::no-loc(constexpr):::`** Funktion zum Zeitpunkt der Kompilierung ausgewertet wird, indem Sie einen Haltepunkt einfügen. Wenn der Haltepunkt erreicht wird, wurde die Funktion zur Laufzeit aufgerufen.  Wenn dies nicht der Fall ist, wurde die Funktion zum Zeitpunkt der Kompilierung aufgerufen.

## <a name="extern-no-locconstexpr"></a>Extern:::no-loc(constexpr):::

Die [/Zc: externconstexpr](../build/reference/zc-extern:::no-loc(constexpr):::.md) -Compileroption bewirkt, dass der Compiler [externe Verknüpfungen](../c-language/external-linkage.md) auf Variablen anwendet, die mit **extern :::no-loc(constexpr)::: **deklariert werden. In früheren Versionen von Visual Studio wendet Visual Studio standardmäßig entweder standardmäßig oder wenn **/Zc: externconstexpr-** die Spezifikation ist :::no-loc(if)::: , eine interne Verknüpfung auf Variablen an, **`:::no-loc(constexpr):::`** auch wenn das **`extern`** Schlüsselwort verwendet wird. Die Option **/Zc: externconstexpr** ist ab Visual Studio 2017 Update 15,6 verfügbar und ist standardmäßig deaktiviert. Die [/permissive-](../build/reference/permissive-standards-con:::no-loc(for):::mance.md) -Option aktiviert **/Zc: externconstexpr**nicht.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt **`:::no-loc(constexpr):::`** Variablen, Funktionen und einen benutzerdefinierten Typ. In der letzten Anweisung in `main()` ist die **`:::no-loc(constexpr):::`** Member-Funktion `GetValue()` ein Lauf Zeit Aufruf, da der Wert zur Kompilierzeit nicht bekannt sein muss.

```cpp
// :::no-loc(constexpr):::.cpp
// Compile with: cl /EHsc /W4 :::no-loc(constexpr):::.cpp
#include <iostream>

using namespace std;

// Pass by value
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
:::no-loc(constexpr)::: float exp2(:::no-loc(const)::: float& x, :::no-loc(const)::: int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
:::no-loc(constexpr)::: int length(:::no-loc(const)::: T(&)[N])
{
    return N;
}

// Recursive :::no-loc(constexpr)::: function
:::no-loc(constexpr)::: int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    :::no-loc(constexpr)::: explicit Foo(int i) : _i(i) {}
    :::no-loc(constexpr)::: int GetValue() :::no-loc(const):::
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is :::no-loc(const)::::
    :::no-loc(constexpr)::: Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    :::no-loc(constexpr)::: float x = exp(5, 3);
    :::no-loc(constexpr)::: float y { exp(2, 5) };
    :::no-loc(constexpr)::: int val = foo.GetValue();
    :::no-loc(constexpr)::: int f5 = fac(5);
    :::no-loc(const)::: int nums[] { 1, 2, 3, 4 };
    :::no-loc(const)::: int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

Visual Studio 2015 oder höher.

## <a name="see-also"></a>Siehe auch

[Deklarationen und Definitionen](../cpp/declarations-and-definitions-cpp.md)\
[:::no-loc(const):::](../cpp/:::no-loc(const):::-cpp.md)
