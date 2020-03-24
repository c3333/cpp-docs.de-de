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
ms.openlocfilehash: e640d18dc3755385188e166c57ad5e912ac24fb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160592"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Unärer Plus- und Negationsoperatoren: + und -

## <a name="syntax"></a>Syntax

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+-Operator

Das Ergebnis des unären plus-Operators ( **+** ) ist der Wert seines Operanden. Der Operand für den unären Plus-Operator muss ein arithmetischer Typ sein.

Ganzzahlige Erweiterung wird für ganzzahlige Operanden ausgeführt. Der resultierende Typ ist der Typ, in den der Operand heraufgestuft wird. Folglich ergibt der Ausdruck `+ch`, wobei `ch` vom Typ **char**ist, den Typ **int**. der Wert ist unverändert. Weitere Informationen zur Ausführung der herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

## <a name="--operator"></a>--Operator

Der unäre Negations Operator ( **-** ) erzeugt den negativen Wert seines Operanden. Der Operand für den unären Negationsoperator muss ein arithmetischer Typ sein.

Ganzzahlige Erweiterung wird für ganzzahlige Operanden durchgeführt, und der resultierende Typ ist der Typ, auf den der Operand erweitert wird. Weitere Informationen zur Durchführung der herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

**Microsoft-spezifisch**

Eine unäre Negation von Mengen ohne Vorzeichen wird ausgeführt, indem der Wert des Operanden von 2^n subtrahiert wird, wobei n die Anzahl von Bits in einem Objekt des angegebenen vorzeichenlosen Typs ist.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
