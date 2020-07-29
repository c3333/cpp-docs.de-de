---
title: 'Unärer Plus- und Negationsoperatoren: + und -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: de90cd2068f9b701167a340fe0b335e2a6c93102
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225799"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Unärer Plus- und Negationsoperatoren: + und -

## <a name="syntax"></a>Syntax

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+-Operator

Das Ergebnis des unären plus-Operators ( **+** ) ist der Wert seines Operanden. Der Operand für den unären Plus-Operator muss ein arithmetischer Typ sein.

Ganzzahlige Erweiterung wird für ganzzahlige Operanden ausgeführt. Der resultierende Typ ist der Typ, in den der Operand heraufgestuft wird. Daher ergibt der Ausdruck `+ch` , wobei `ch` vom Typ ist **`char`** , **`int`** den Typ. der Wert ist unverändert. Weitere Informationen zur Ausführung der herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

## <a name="--operator"></a>--Operator

Der unäre Negations Operator ( **-** ) erzeugt den negativen Wert seines Operanden. Der Operand für den unären Negationsoperator muss ein arithmetischer Typ sein.

Ganzzahlige Erweiterung wird für ganzzahlige Operanden durchgeführt, und der resultierende Typ ist der Typ, auf den der Operand erweitert wird. Weitere Informationen zur Durchführung der herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

**Microsoft-spezifisch**

Eine unäre Negation von Mengen ohne Vorzeichen wird ausgeführt, indem der Wert des Operanden von 2^n subtrahiert wird, wobei n die Anzahl von Bits in einem Objekt des angegebenen vorzeichenlosen Typs ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
