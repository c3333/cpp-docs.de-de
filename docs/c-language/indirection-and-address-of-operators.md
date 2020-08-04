---
title: Dereferenzierungs- und Address-of-Operatoren
ms.date: 02/16/2018
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
ms.openlocfilehash: e631959e69fbdf026886b7a67a3d4e4cd7266989
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229635"
---
# <a name="indirection-and-address-of-operators"></a>Dereferenzierungs- und Address-of-Operatoren

Der unäre Dereferenzierungsoperator ( __&#42;__ ) greift indirekt über einen Zeiger auf einen Wert zu. Der Operand muss ein Zeigertyp sein. Das Ergebnis des Vorgangs ist der Wert, der vom Operanden adressiert wird, also der Wert bei der Adresse, auf die der Operand zeigt. Der Typ, den der Operand adressiert, ist der Ergebnistyp.

Das Ergebnis des Dereferenzierungsoperators ist *type*, wenn der Operand vom Typ *pointer to type* ist. Wenn der Operand auf eine Funktion verweist, ist das Ergebnis ein Funktionsbezeichner. Wenn er auf ein Objekt zeigt, ist das Ergebnis ein lvalue, der das Objekt festlegt.

Wenn der Zeigerwert unzulässig ist, ist das Ergebnis des Dereferenzierungsoperators nicht definiert. Hier sehen Sie einige der häufigsten Bedingungen, die einen Zeigerwert ungültig machen:

- Der Zeiger ist ein NULL-Zeiger.

- Der Zeiger gibt die Adresse eines Objekts nach dem Ende seines Lebenszyklus zur Zeit des Verweises an (z.B. ein Objekt, das sich nicht mehr im Bereich befindet oder dessen Zuordnung aufgehoben wurde).

- Der Zeiger gibt eine Adresse an, die nicht ordnungsgemäß auf den Objekttyp, auf den gezeigt wird, ausgerichtet ist.

- Der Zeiger gibt eine Adresse an, die nicht vom ausgeführten Programm verwendet wird.

Der unäre address-of-Operator ( **&** ) gibt die Adresse seines Operanden aus. Der Operand muss entweder ein lvalue sein, der ein Objekt angibt, das nicht als __Register__ deklariert wurde und kein Bitfeld ist, oder das Ergebnis eines unären __&#42;__ -Operators oder eines Arraydereferenzierungsoperators ( __&#91;&#93;__ ) oder ein Funktionsdesignator sein. Das Ergebnis ist für einen Operanden des Typs *type* vom Typ *pointer to type*.

Wenn der Operand das Ergebnis eines unären __&#42;__ -Operators ist, wird keiner der Operatoren ausgewertet, und das Ergebnis ist so, als seien beide übersprungen worden. Das Ergebnis ist kein lvalue, und die Einschränkungen der Operatoren gelten weiterhin. Wenn der Operand das Ergebnis eines __&#91;&#93;__ -Operators ist, wird weder der __&__ -Operator noch der unäre __&#42;__ -Operator, die vom __&#91;&#93;__ -Operator impliziert werden, ausgewertet. Das Ergebnis hat die gleichen Auswirkungen wie das Entfernen des __&__ -Operators und das Ändern des __&#91;&#93;__ -Operators in einen __+__ -Operator. Andernfalls ist das Ergebnis ein Zeiger auf ein Objekt oder eine Funktion, die vom Operanden festgelegt wird.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden diese gängigen Deklarationen verwendet:

```C
int *pa, x;
int a[20];
double d;
```

Die Anweisung verwendet den address-of-Operator ( **&** ), um die Adresse des sechsten Elements des `a`-Arrays abzurufen. Das Ergebnis wird in der Zeigervariable `pa` gespeichert:

```C
pa = &a[5];
```

Der Dereferenzierungsoperator ( __&#42;__ ) wird in diesem Beispiel verwendet, um auf den Wert **`int`** an der in `pa` gespeicherten Adresse zuzugreifen. Der Wert wird der ganzzahligen `x`-Variable zugewiesen:

```C
x = *pa;
```

Dieses Beispiel zeigt, dass das Ergebnis der Anwendung des Dereferenzierungsoperators auf die Adresse von `x` dasselbe wie bei `x` ist:

```C
assert( x == *&x );
```

In diesem Beispiel werden ähnliche Methoden zum Deklarieren eines Zeigers auf eine Funktion gezeigt:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Sobald die Funktion `roundup` deklariert ist, werden zwei Zeiger auf `roundup` deklariert und initialisiert. Der erste Zeiger `proundup` wird unter ausschließlicher Verwendung des Namens der Funktion initialisiert, während der zweite Zeiger `pround` den address-of-Operator bei der Initialisierung verwendet. Die Initialisierungen entsprechen sich.

## <a name="see-also"></a>Siehe auch

[Dereferenzierungsoperator: &#42;](../cpp/indirection-operator-star.md)<br/>
[address-of-Operator](../cpp/address-of-operator-amp.md)
