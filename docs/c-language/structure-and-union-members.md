---
title: Struktur- und Unionmember
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
ms.openlocfilehash: b22f5a29a4dc088ea4f3db863d635badee048d2c
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825690"
---
# <a name="structure-and-union-members"></a>Struktur- und Unionmember

Ein Memberauswahlausdruck bezieht sich auf Member von Strukturen und Unions. Ein solcher Ausdruck hat den Wert und Typ des ausgewählten Members.

> *postfix-Ausdruck* **.** *Bezeichner*\
> *postfix-Ausdruck* **->** *Bezeichner*

Diese Liste beschreibt die zwei Arten von Memberauswahlausdrücken:

1. Im ersten Formular steht *postfix-expression* für einen Wert des Typs **struct** oder **union**; mit *identifier* wird ein Member der angegebenen Struktur oder Union benannt. Der Wert des Vorgangs entspricht *identifier* und ist ein L-Wert, sofern *postfix-expression* ein L-Wert ist. Weitere Informationen finden Sie unter [L-Wert-und R-Wert-Ausdrücke](../c-language/l-value-and-r-value-expressions.md).

1. Im zweiten Formular steht *postfix-expression* für einen Zeiger auf eine Struktur oder Union; mit *identifier* wird ein Member der angegebenen Struktur oder Union benannt. Der Wert entspricht *identifier* und ist ein L-Wert.

Die beiden Formen der Memberauswahlausdrücke verfügen über ähnliche Auswirkungen.

Tatsächlich ist ein Ausdruck, der den Memberauswahloperator ( **->** ) enthält, eine Kurznotationsversion eines Ausdrucks, der den Punkt ( **.** ) verwendet, wenn der Ausdruck vor dem Punkt aus dem Dereferenzierungsoperator (<strong>\*</strong>) besteht, der auf einen Zeigerwert angewendet wird. Daher eignet sich

```cpp
expression->identifier
```

für die folgende Syntax:

```cpp
(*expression).identifier
```

wenn *expression* ein Zeigerwert ist

## <a name="examples"></a>Beispiele

Die folgenden Beispiele beziehen sich auf diese Strukturdeklaration. Weitere Informationen zum Dereferenzierungsoperator (<strong>\*</strong>), der in diesen Beispielen verwendet wird, finden Sie unter [Dereferenzierungs- und Address-of-Operatoren](../c-language/indirection-and-address-of-operators.md).

```
struct pair
{
    int a;
    int b;
    struct pair *sp;
} item, list[10];
```

Ein Memberauswahlausdruck für die `item`-Struktur sieht wie folgt aus:

```
item.sp = &item;
```

Im obigen Beispiel wird die Adresse der `item`-Struktur dem `sp`-Member der Struktur zugewiesen. Dies bedeutet, dass `item` einen Zeiger auf sich selbst enthält.

```
(item.sp)->a = 24;
```

In diesem Beispiel wird der Zeigerausdruck `item.sp` mit dem Memberauswahloperator ( **->** ) verwendet, um dem Member `a` einen Wert zuzuweisen.

```
list[8].b = 12;
```

Diese Anweisung zeigt, wie ein einzelner Strukturmember aus einem Array von Strukturen ausgewählt wird.

## <a name="see-also"></a>Siehe auch

[Operatoren für den Memberzugriff: . und ->](../cpp/member-access-operators-dot-and.md)
