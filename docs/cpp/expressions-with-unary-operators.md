---
title: Ausdrücke mit unären Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 26aad64e5b9c7a496c2e6bb131b82740c06abe07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188973"
---
# <a name="expressions-with-unary-operators"></a>Ausdrücke mit unären Operatoren

Unäre Operatoren werden nur auf einen Operanden in einem Ausdruck angewendet. Die unären Operatoren lauten wie folgt:

- [Dereferenzierungsoperator (*)](../cpp/indirection-operator-star.md)

- [Address-of-Operator (&)](../cpp/address-of-operator-amp.md)

- [Unärer Plus-Operator (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Unärer Negations Operator (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Logischer Negations Operator (!)](../cpp/logical-negation-operator-exclpt.md)

- [Einerkomplement Operator (~)](../cpp/one-s-complement-operator-tilde.md)

- [Prefix-Inkrementoperator (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Prefix-Dekrementoperator (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Umwandlungs Operator ()](../cpp/cast-operator-parens.md)

- [sizeof (Operator)](../cpp/sizeof-operator.md)

- [__uuidof-Operator](../cpp/uuidof-operator.md)

- [__alignof-Operator](../cpp/alignof-operator.md)

- [New-Operator](../cpp/new-operator-cpp.md)

- [Delete-Operator](../cpp/delete-operator-cpp.md)

Diese Operatoren weisen eine Assoziativität von rechts nach links auf. Unäre Ausdrücke umfassen im Allgemeinen Syntax, die einem Postfix oder primären Ausdruck vorausgeht.

Folgende Formen von unären Ausdrücken sind möglich:

- *postfix-expression*

- *unärer Ausdruck* `++`

- *unärer Ausdruck* `--`

- *Cast-Expression* ( *unary-Operator* )

- **sizeof** *unary-expression*

- `sizeof(` *Type-Name* `)`

- `decltype(` *Ausdrucks* `)`

- *Allocation-Ausdruck*

- *Aufhebung der Zuordnung-Ausdruck*

*Postfix-Expression* wird als *unärer Ausdruck*betrachtet, und da jeder primäre Ausdruck als *Postfix-Expression*angesehen wird, werden alle primären Ausdrücke auch als *unärer* Ausdruck angesehen. Weitere Informationen finden Sie unter [Postfix Ausdrücke](../cpp/postfix-expressions.md) und [primäre Ausdrücke](../cpp/primary-expressions.md).

Ein *unärer Operator* besteht aus einem oder mehreren der folgenden Symbole: `* & + - ! ~`

*Cast-Expression* ist ein unärer Ausdruck mit einer optionalen Umwandlung, um den Typ zu ändern. Weitere Informationen finden Sie unter [Cast Operator: ()](../cpp/cast-operator-parens.md).

Ein *Ausdruck* kann ein beliebiger Ausdruck sein. Weitere Informationen finden Sie unter [Ausdrücke](../cpp/expressions-cpp.md).

Der *Zuordnungs Ausdruck* bezieht sich auf den **New** -Operator. Der *Ausdruck "Aufteilungs Ausdruck* " bezieht sich auf den **Delete** -Operator. Weitere Informationen finden Sie unter den Links weiter oben in diesem Thema.

## <a name="see-also"></a>Weitere Informationen

[Ausdruckstypen](../cpp/types-of-expressions.md)
