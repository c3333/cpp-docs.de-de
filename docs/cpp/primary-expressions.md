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
ms.openlocfilehash: 03f0d0d04ad8ef2b052b9303d15437c53369a003
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177624"
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

Das **this** -Schlüsselwort ist ein Zeiger auf ein Klassenobjekt. Es ist innerhalb von nicht statische Memberfunktionen verfügbar und zeigt auf die Instanz der Klasse, für die die Funktion aufgerufen wurde. Das **this** -Schlüsselwort kann nicht außerhalb des Texts einer Klassenmember-Funktion verwendet werden.

Der Typ des **this** -Zeigers ist `type` **\*Konstanten** (wobei `type` der Klassenname ist) innerhalb von Funktionen, die den **this** -Zeiger nicht explizit verändern. Im folgenden Beispiel werden Member-Funktions Deklarationen und die folgenden Typen **angezeigt:**

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

Weitere Informationen zum Ändern des Typs des **this** -Zeigers finden Sie in [diesem Zeiger](this-pointer.md) .

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

## <a name="see-also"></a>Weitere Informationen

[Ausdruckstypen](../cpp/types-of-expressions.md)
