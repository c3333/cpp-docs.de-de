---
title: C++Integrierte Operatoren, Rangfolge und Assoziativität
ms.date: 11/04/2016
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180406"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++Integrierte Operatoren, Rangfolge und Assoziativität

Die Sprache C++ umfasst alle C-Operatoren und fügt mehrere neue Operatoren hinzu. Operatoren legen eine Bewertung fest, die an einem oder mehreren Operanden auszuführen ist.

Operator *Rangfolge* gibt die Reihenfolge der Vorgänge in Ausdrücken an, die mehr als einen Operator enthalten. Operator *Assoziativität* gibt an, ob in einem Ausdruck, der mehrere Operatoren mit der gleichen Rangfolge enthält, ein Operand auf der linken Seite oder auf der rechten Seite des Operators gruppiert wird. Die folgende Tabelle zeigt die Rangfolge und Assoziativität von C++-Operatoren (in absteigender Rangfolge). Operatoren mit derselben Rangfolgenzahl haben die gleiche Rangfolge, es sei denn, es wird eine andere Beziehung explizit durch Klammern erzwungen.

### <a name="c-operator-precedence-and-associativity"></a>C++-Operatorrangfolge und Assoziativität

|Operatorbeschreibung|Operator|
|--------------------------|--------------|
|**Rangfolge der Gruppe 1, keine Assoziativität**|
|[Bereichs Auflösung](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Priorität der Gruppe 2, links-nach-rechts-Assoziativität**|
|[Elementauswahl (Objekt oder Zeiger)](../cpp/member-access-operators-dot-and.md)|[. oder->](../cpp/member-access-operators-dot-and.md)|
|[Array Index](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Funktionsaufrufe](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Postfix-Inkrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Postfix Dekrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Typname](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Konstante Typkonvertierung](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Dynamische Typkonvertierung](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Neu interpretierte Typkonvertierung](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Statische Typkonvertierung](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Gruppe 3-Rangfolge, von rechts nach links Assoziativität**|
|[Größe des Objekts oder Typs](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Präfix Inkrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Präfix Dekrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Einerkomplement](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logisches NOT](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Unäre Negation](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Unäres Plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adresse-von](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Dereferenzierung](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Create object](../cpp/new-operator-cpp.md) (Objekt erstellen)|[Neu](../cpp/new-operator-cpp.md)|
|[Objekt zerstören](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Umwandeln](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorität der Gruppe 4, von links nach rechts Assoziativität**|
|[Zeiger auf Member (Objekte oder Zeiger)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; oder->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorität der Gruppe 5, links-nach-rechts-Assoziativität**|
|[Multiplikation](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Division](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorität der Gruppe 6, von links nach rechts Assoziativität**|
|[Addition](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Subtraktion](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Gruppen 7-Rangfolge, von links nach rechts Assoziativität**|
|[Nach links verschieben](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Rechte Verschiebung](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Rangfolge der Gruppe 8, von links nach rechts Assoziativität**|
|[Kleiner als](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Größer als](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Kleiner gleich](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Größer gleich](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Group 9-Rangfolge, von links nach rechts Assoziativität**|
|[Gleichheit](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Ungleichheit](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Gruppe 10 hat Vorrang vor der rechten Assoziativität**|
|[Bitweises AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Gruppe 11, Rangfolge, links-nach-rechts-Assoziativität**|
|[Bitweises exklusives OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Priorität der Gruppe 12, von links nach rechts Assoziativität**|
|[Bitweises inklusives OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Gruppe 13, Rangfolge, links-nach-rechts-Assoziativität**|
|[Logisches AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Gruppe 14 Rangfolge, links-nach-rechts-Assoziativität**|
|[Logisches OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Gruppe 15 Rangfolge, von rechts nach links Assoziativität**|
|[Conditional](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Gruppe 16 Rangfolge, von rechts nach links Assoziativität**|
|[Zuweisung](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Multiplikations Zuweisung](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Divisions Zuweisung](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Modulozuweisung](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Additions Zuweisung](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Subtraktions Zuweisung](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Links Schiebe Zuweisung](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Rechts Schiebe Zuweisung](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Bitweise AND-Zuweisung](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bitweise inklusive OR-Zuweisung](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitweise exklusive OR-Zuweisung](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Gruppe 17 Rangfolge, von rechts nach links Assoziativität**|
|[Throw-Ausdruck](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Gruppe 18 Rangfolge, links-nach-rechts-Assoziativität**|
|[Komma](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Weitere Informationen

[Operatorüberladung](operator-overloading.md)
