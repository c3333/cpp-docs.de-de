---
title: Eindimensionale Arrays
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: c310d610b4e4cfc5ae5620d38337a5b8fd5243ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226352"
---
# <a name="one-dimensional-arrays"></a>Eindimensionale Arrays

Ein Postfixausdruck, gefolgt von einem Ausdruck in eckigen Klammern ( **[ ]** ), ist eine indizierte Darstellung eines Elements eines Arrayobjekts. Ein Indexausdruck stellt den Wert an der Adresse dar, welche die *expression* hinter *postfix-expression* positioniert, wenn diese ausgedrückt wird als

```
postfix-expression [ expression ]
```

Normalerweise ist der von *postfix-expression* dargestellte Wert ein Zeigerwert, z. B. ein Arraybezeichner, und *expression* ist ein Ganzzahlwert. Syntaktisch erforderlich ist allerdings nur, dass einer der Ausdrücke vom Zeigertyp und der andere Ausdruck vom Ganzzahltyp ist. Daher kann der ganzzahlige Wert an der *postfix-expression*-Position sein, und der Zeigerwert kann in eckigen Klammern an der *expression*- oder der „Index“-Position sein. Beispielsweise ist folgender Code gültig:

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Indexausdrücke werden im Allgemeinen verwendet, um auf Arrayelemente zu verweisen. Sie können einen Index jedoch auf jeden Zeiger anwenden. Ungeachtet der Reihenfolge der Werte muss *expression* in eckige Klammern ( **[ ]** ) eingeschlossen werden.

Der Indexausdruck wird ausgewertet, indem der Zeigerwert zum ganzzahligen Wert hinzugefügt wird, bevor der Dereferenzierungsoperator (<strong>\*</strong>) auf das Ergebnis angewandt wird. (Eine Erläuterung des Dereferenzierungsoperators finden Sie unter [Dereferenzierungs- und Address-of-Operatoren](../c-language/indirection-and-address-of-operators.md).) Für ein eindimensionales Array sind die folgenden vier Ausdrücke gleichwertig, vorausgesetzt, dass `a` ein Zeiger ist und `b` eine ganze Zahl darstellt:

```
a[b]
*(a + b)
*(b + a)
b[a]
```

Gemäß den Konvertierungsregeln für den Additionsoperator (angegeben in [Additive Operators](../c-language/c-additive-operators.md) [Additive Operatoren]), wird der Ganzzahlwert in einen Adressoffset konvertiert, indem er durch die Länge des Typs multipliziert wird, der vom Zeiger adressiert wird.

Nehmen Sie z. B. an, der Bezeichner `line` verweist auf ein Array von **`int`** -Werten. Der Indexausdruck `line[ i ]` wird mit folgendem Verfahren ausgewertet:

1. Der Integerwert `i` wird mit der Zahl der Bytes, die als die Länge eines **`int`** -Elements definiert ist, multipliziert. Der konvertierte Wert von `i` stellt `i` **`int`** -Positionen dar.

1. Dieser konvertierte Wert wird dem ursprünglichen Zeigerwert (`line`) hinzugefügt, um eine Adresse zu erhalten, die um `i` **`int`** -Positionen von `line` versetzt ist.

1. Der Dereferenzierungsoperator wird auf die neue Adresse angewendet. Das Ergebnis ist der Wert des Arrayelements an dieser Position (intuitiv `line [ i ]`).

Der Indexausdruck `line[0]` stellt den Wert des ersten Elements der Zeile dar, da der Offset der Adresse, die von `line` dargestellt wird, 0 ist. Gleichermaßen verweist ein Ausdruck wie `line[5]` auf den Elementoffset fünf Positionen ab der Zeile oder auf das sechste Element des Arrays.

## <a name="see-also"></a>Siehe auch

[Subscript-Operator: ](../cpp/subscript-operator.md)
