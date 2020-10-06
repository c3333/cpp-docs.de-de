---
title: Primäre Ausdrücke
description: Primäre Ausdrücke in der Programmiersprache C++.
ms.date: 10/02/2020
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 4c52992071453bc189a3078db9592b02dfb8ba9b
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765319"
---
# <a name="primary-expressions"></a>Primärausdrücke

Primäre Ausdrücke sind die Bausteine für komplexere Ausdrücke. Dabei kann es sich um Literale, Namen und Namen handeln, die durch den Bereichs Auflösungs Operator () qualifiziert werden `::` . Ein primärer Ausdruck kann jede der folgenden Formen haben:

*`primary-expression`*\
&emsp;*`literal`*\
&emsp;**`this`**\
&emsp;*`name`*\
&emsp;**`::`** *`name`* **`(`** *`expression`* **`)`**

Ein *`literal`* ist ein konstanter primärer Ausdruck. Sein Typ hängt von der Form seiner Spezifikation ab. Ausführliche Informationen zum Angeben von literalen finden Sie unter [Literale](../cpp/numeric-boolean-and-pointer-literals-cpp.md) .

Das **`this`** Schlüsselwort ist ein Zeiger auf ein Klassenobjekt. Sie steht in nicht statischen Element Funktionen zur Verfügung. Er verweist auf die Instanz der-Klasse, für die die Funktion aufgerufen wurde. Das **`this`** Schlüsselwort kann nicht außerhalb des Texts einer Klassenmember-Funktion verwendet werden.

Der Typ des **`this`** Zeigers ist `type * const` (wobei `type` der Klassenname ist) innerhalb von Funktionen, die den Zeiger nicht explizit ändern **`this`** . Im folgenden Beispiel werden Member-Funktions Deklarationen und die Typen von veranschaulicht **`this`** :

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

Weitere Informationen zum Ändern des Zeiger Typs finden Sie **`this`** unter [ `this` Zeiger](this-pointer.md).

Der Bereichs Auflösungs Operator ( **`::`** ), gefolgt von einem Namen, ist ein primärer Ausdruck.  Solche Namen müssen Namen von globaler Reichweite sein, nicht Membernamen. Der Typ des Ausdrucks wird durch die Deklaration des Namens bestimmt. Dabei handelt es sich um einen l-Wert (d. h., er kann auf der linken Seite eines Zuweisungs Ausdrucks angezeigt werden), wenn der deklarierende Name ein l-Wert ist. Der Bereichsauflösungsoperator lässt zu, dass auf einen globalen Namen verwiesen wird, selbst wenn dieser Name im aktuellen Bereich ausgeblendet ist. Ein Beispiel für die Verwendung des Bereichs Auflösungs Operators finden Sie unter [Scope](../cpp/scope-visual-cpp.md) .

Ein Ausdruck, der in Klammern eingeschlossen ist, ist ein primärer Ausdruck. Der Typ und der Wert sind mit dem Typ und dem Wert des Ausdrucks ohne Klammer identisch. Es ist ein l-Wert, wenn der Ausdruck ohne Klammer einen l-Wert ist.

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

Diese Beispiele gelten als *Namen*und als solche primär Ausdrücke in verschiedenen Formen:

```cpp
MyClass // an identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>Siehe auch

[Ausdrucks Typen](../cpp/types-of-expressions.md)
