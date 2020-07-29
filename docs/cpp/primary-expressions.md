---
title: Primärausdrücke
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: c827f811813091abc62d07f12ac387bc2a0a0cc5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231142"
---
# <a name="primary-expressions"></a>Primärausdrücke

Primäre Ausdrücke sind die Bausteine für komplexere Ausdrücke. Es handelt sich um Literale, Namen und Namen, die vom Bereichsauflösungsoperator (`::`) qualifiziert werden.  Ein primärer Ausdruck kann jede der folgenden Formen haben:

```
literal
this
name
::name ( expression )
```

Ein *Literalausdruck* ist ein konstanter primärer Ausdruck. Sein Typ hängt von der Form seiner Spezifikation ab. Ausführliche Informationen zum Angeben von literalen finden Sie unter [Literale](../cpp/numeric-boolean-and-pointer-literals-cpp.md) .

Das **`this`** Schlüsselwort ist ein Zeiger auf ein Klassenobjekt. Es ist innerhalb von nicht statische Memberfunktionen verfügbar und zeigt auf die Instanz der Klasse, für die die Funktion aufgerufen wurde. Das **`this`** Schlüsselwort kann nicht außerhalb des Texts einer Klassenmember-Funktion verwendet werden.

Der Typ des **`this`** Zeigers ist " `type` ** \* Konstanten** " (wobei `type` der Klassenname ist) innerhalb von Funktionen, die nicht explizit den **`this`** Zeiger ändern. Im folgenden Beispiel werden Member-Funktions Deklarationen und die Typen von veranschaulicht **`this`** :

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

Weitere Informationen zum Ändern des Zeiger Typs finden Sie in [diesem Zeiger](this-pointer.md) **`this`** .

Der Bereichsauflösungsoperator (`::`) gefolgt von einem Namen stellt einen primären Ausdruck dar.  Solche Namen müssen Namen von globaler Reichweite sein, nicht Membernamen.  Der Typ dieses Ausdrucks wird durch die Deklaration des Namens bestimmt. Es ist ein l-Wert (das heißt, er kann auf der linken Seite eines Zuweisungsoperatorausdrucks angezeigt werden), wenn der deklarierende Name ein l-Wert ist. Der Bereichsauflösungsoperator lässt zu, dass auf einen globalen Namen verwiesen wird, selbst wenn dieser Name im aktuellen Bereich ausgeblendet ist. Ein Beispiel für die Verwendung des Bereichs Auflösungs Operators finden Sie unter [Scope](../cpp/scope-visual-cpp.md) .

Ein in Klammern eingefasster Ausdruck ist ein primärer Ausdruck, dessen Typ und Wert mit denen des nicht in Klammern stehenden Ausdrucks identisch sind. Es ist ein l-Wert, wenn der nicht in Klammern stehende Ausdruck ein l-Wert ist.

Zu den Beispielen von primären Ausdrücken gehören:

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

In den folgenden Beispielen werden alle als *Namen*und daher primäre Ausdrücke in verschiedenen Formen aufgeführt:

```cpp
MyClass // a identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>Siehe auch

[Ausdrucks Typen](../cpp/types-of-expressions.md)
