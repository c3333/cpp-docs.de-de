---
title: C++ integrierte Operatoren, Rangfolge und Assoziativität
ms.date: 07/23/2020
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 10c9e5db569ba211ed8d42386816b4f6bb71ee29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221769"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++ integrierte Operatoren, Rangfolge und Assoziativität

Die Sprache C++ umfasst alle C-Operatoren und fügt mehrere neue Operatoren hinzu. Operatoren legen eine Bewertung fest, die an einem oder mehreren Operanden auszuführen ist.

## <a name="precedence-and-associativity"></a>Rangfolge und Assoziativität

Operator *Rangfolge* gibt die Reihenfolge der Vorgänge in Ausdrücken an, die mehr als einen Operator enthalten. Operator *Assoziativität* gibt an, ob in einem Ausdruck, der mehrere Operatoren mit der gleichen Rangfolge enthält, ein Operand auf der linken Seite oder auf der rechten Seite des Operators gruppiert wird.

## <a name="alternative-spellings"></a>Alternative rechtschreibweisen

C++ gibt alternative rechtschreibweisen für einige Operatoren an. In C werden die alternativen rechtschreibweisen als Makros in der \<iso646.h> Kopfzeile bereitgestellt. In C++ handelt es sich bei diesen Alternativen um Schlüsselwörter, und die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption zum Aktivieren der alternativen Rechtschreibprüfung erforderlich.

## <a name="c-operator-precedence-and-associativity-table"></a>C++ Operator Rangfolge und Assoziativität-Tabelle

Die folgende Tabelle zeigt die Rangfolge und Assoziativität von C++-Operatoren (in absteigender Rangfolge). Operatoren mit derselben Rangfolgenzahl haben die gleiche Rangfolge, es sei denn, es wird eine andere Beziehung explizit durch Klammern erzwungen.

| Operatorbeschreibung | Operator | Alternative |
|--|--|--|
| **Rangfolge der Gruppe 1, keine Assoziativität** |
| [Bereichs Auflösung](../cpp/scope-resolution-operator.md) | [`::`](../cpp/scope-resolution-operator.md) |
| **Priorität der Gruppe 2, links-nach-rechts-Assoziativität** |
| [Memberauswahl (Objekt oder Zeiger)](../cpp/member-access-operators-dot-and.md) | [`.`noch`->`](../cpp/member-access-operators-dot-and.md) |
| [Array-Subscript](../cpp/subscript-operator.md) | [`[]`](../cpp/subscript-operator.md) |
| [Funktionsaufruf](../cpp/function-call-operator-parens.md) | [`()`](../cpp/function-call-operator-parens.md) |
| [Postfixinkrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Postfixdekrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Typname](../cpp/typeid-operator.md) | [`typeid`](../cpp/typeid-operator.md) |
| [Konstantentypkonvertierung](../cpp/const-cast-operator.md) | [`const_cast`](../cpp/const-cast-operator.md) |
| [Dynamische Typkonvertierung](../cpp/dynamic-cast-operator.md) | [`dynamic_cast`](../cpp/dynamic-cast-operator.md) |
| [Neu interpretierte Typkonvertierung](../cpp/reinterpret-cast-operator.md) | [`reinterpret_cast`](../cpp/reinterpret-cast-operator.md) |
| [Statische Typkonvertierung](../cpp/static-cast-operator.md) | [`static_cast`](../cpp/static-cast-operator.md) |
| **Gruppe 3-Rangfolge, von rechts nach links Assoziativität** |
| [Größe des Objekts oder Typs](../cpp/sizeof-operator.md) | [`sizeof`](../cpp/sizeof-operator.md) |
| [Präfixinkrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Präfixdekrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Einerkomplement](../cpp/one-s-complement-operator-tilde.md) | [`~`](../cpp/one-s-complement-operator-tilde.md) | **`compl`** |
| [Logisches NOT](../cpp/logical-negation-operator-exclpt.md) | [`!`](../cpp/logical-negation-operator-exclpt.md) | **`not`** |
| [Unäre Negation](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`-`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Unäres Plus](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`+`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Address-of](../cpp/address-of-operator-amp.md) | [`&`](../cpp/address-of-operator-amp.md) |
| [Dereferenzierung](../cpp/indirection-operator-star.md) | [`*`](../cpp/indirection-operator-star.md) |
| [Objekt erstellen](../cpp/new-operator-cpp.md) | [`new`](../cpp/new-operator-cpp.md) |
| [Objekt zerstören](../cpp/delete-operator-cpp.md) | [`delete`](../cpp/delete-operator-cpp.md) |
| [Darsteller](../cpp/cast-operator-parens.md) | [`()`](../cpp/cast-operator-parens.md) |
| **Priorität der Gruppe 4, von links nach rechts Assoziativität** |
| [Pointer-to-member (Objekte oder Zeiger)](../cpp/pointer-to-member-operators-dot-star-and-star.md) | [`.*`noch`->*`](../cpp/pointer-to-member-operators-dot-star-and-star.md) |
| **Priorität der Gruppe 5, links-nach-rechts-Assoziativität** |
| [Multiplikation](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`*`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Division](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`/`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Modulus](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`%`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| **Priorität der Gruppe 6, von links nach rechts Assoziativität** |
| [Addition](../cpp/additive-operators-plus-and.md) | [`+`](../cpp/additive-operators-plus-and.md) |
| [Subtraktion](../cpp/additive-operators-plus-and.md) | [`-`](../cpp/additive-operators-plus-and.md) |
| **Gruppen 7-Rangfolge, von links nach rechts Assoziativität** |
| [Nach links verschieben](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`<<`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| [Rechte Verschiebung](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`>>`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| **Rangfolge der Gruppe 8, von links nach rechts Assoziativität** |
| [Kleiner als](../cpp/relational-operators-equal-and-equal.md) | [`<`](../cpp/relational-operators-equal-and-equal.md) |
| [Größer als](../cpp/relational-operators-equal-and-equal.md) | [`>`](../cpp/relational-operators-equal-and-equal.md) |
| [Kleiner als oder gleich](../cpp/relational-operators-equal-and-equal.md) | [`<=`](../cpp/relational-operators-equal-and-equal.md) |
| [Größer als oder gleich](../cpp/relational-operators-equal-and-equal.md) | [`>=`](../cpp/relational-operators-equal-and-equal.md) |
| **Group 9-Rangfolge, von links nach rechts Assoziativität** |
| [Gleichheit](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`==`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) |
| [Ungleichheit](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`!=`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | **`not_eq`** |
| **Gruppe 10 hat Vorrang vor der rechten Assoziativität** |
| [Bitweises AND](../cpp/bitwise-and-operator-amp.md) | [`&`](../cpp/bitwise-and-operator-amp.md) | **`bitand`** |
| **Gruppe 11, Rangfolge, links-nach-rechts-Assoziativität** |
| [Bitweises exklusives OR](../cpp/bitwise-exclusive-or-operator-hat.md) | [`^`](../cpp/bitwise-exclusive-or-operator-hat.md) | **`xor`** |
| **Priorität der Gruppe 12, von links nach rechts Assoziativität** |
| [Bitweises inklusives OR](../cpp/bitwise-inclusive-or-operator-pipe.md) | [`|`](../cpp/bitwise-inclusive-or-operator-pipe.md) | **`bitor`** |
| **Gruppe 13, Rangfolge, links-nach-rechts-Assoziativität** |
| [Logisches AND](../cpp/logical-and-operator-amp-amp.md) | [`&&`](../cpp/logical-and-operator-amp-amp.md) | **`and`** |
| **Gruppe 14 Rangfolge, links-nach-rechts-Assoziativität** |
| [Logisches OR](../cpp/logical-or-operator-pipe-pipe.md) | [`||`](../cpp/logical-or-operator-pipe-pipe.md) | **`or`** |
| **Gruppe 15 Rangfolge, von rechts nach links Assoziativität** |
| [Bedingt](../cpp/conditional-operator-q.md) | [`? :`](../cpp/conditional-operator-q.md) |
| **Gruppe 16 Rangfolge, von rechts nach links Assoziativität** |
| [Zuweisung](../cpp/assignment-operators.md) | [`=`](../cpp/assignment-operators.md) |
| [Multiplikationszuweisung](../cpp/assignment-operators.md) | [`*=`](../cpp/assignment-operators.md) |
| [Divisionszuweisung](../cpp/assignment-operators.md) | [`/=`](../cpp/assignment-operators.md) |
| [Modulozuweisung](../cpp/assignment-operators.md) | [`%=`](../cpp/assignment-operators.md) |
| [Additionszuweisung](../cpp/assignment-operators.md) | [`+=`](../cpp/assignment-operators.md) |
| [Subtraktionszuweisung](../cpp/assignment-operators.md) | [`-=`](../cpp/assignment-operators.md) |
| [Linksschiebezuweisung](../cpp/assignment-operators.md) | [`<<=`](../cpp/assignment-operators.md) |
| [Rechtsschiebezuweisung](../cpp/assignment-operators.md) | [`>>=`](../cpp/assignment-operators.md) |
| [Bitweise AND-Zuweisung](../cpp/assignment-operators.md) | [`&=`](../cpp/assignment-operators.md) | **`and_eq`** |
| [Bitweise inklusive OR-Zuweisung](../cpp/assignment-operators.md) | [`|=`](../cpp/assignment-operators.md) | **`or_eq`** |
| [Bitweise exklusive OR-Zuweisung](../cpp/assignment-operators.md) | [`^=`](../cpp/assignment-operators.md) | **`xor_eq`** |
| **Gruppe 17 Rangfolge, von rechts nach links Assoziativität** |
| [Ausdruck auslösen](../cpp/try-throw-and-catch-statements-cpp.md) | [`throw`](../cpp/try-throw-and-catch-statements-cpp.md) |
| **Gruppe 18 Rangfolge, links-nach-rechts-Assoziativität** |
| [Komma](../cpp/comma-operator.md) | [,](../cpp/comma-operator.md) |

## <a name="see-also"></a>Weitere Informationen

[Operatorüberladung](operator-overloading.md)
