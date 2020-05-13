---
title: C-Multiplikationsoperatoren
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: f9f5f62e2326826e3087a8668cd9107da4b85388
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334994"
---
# <a name="c-multiplicative-operators"></a>C-Multiplikationsoperatoren

Die multiplikationsoperatoren führen<strong>\*</strong>Multiplikationsvorgänge ( ), Division (**/**), und Restvorgänge (**%**) aus.

## <a name="syntax"></a>Syntax

*Multiplikativ-Ausdruck* &nbsp; &nbsp; &nbsp; &nbsp;: *Umwandlungsausdruck* &nbsp; &nbsp; &nbsp; &nbsp; *multiplikativ-ausdrucksexpression* <strong>\*</strong> *cast-expression* &nbsp; &nbsp; &nbsp; &nbsp; *multiplikativ-ausdrucksexpression* **/** *multiplizieren-expression* **%** *cast-expression* &nbsp; &nbsp; &nbsp; &nbsp; *multiplizierend-ausdrucksexpression*

Die Operanden des Restoperators**%**( ) müssen integral sein. Die Operatoren<strong>\*</strong>Multiplikation**/**( ) und Division ( ) können integrale oder schwebende Operanden verwenden; die Typen der Operanden können unterschiedlich sein.

Die multiplikativen Operatoren führen die üblichen arithmetischen Konvertierungen für die Operanden aus. Der Ergebnistyp ist der Typ der Operanden nach der Konvertierung.

> [!NOTE]
> Da Konvertierungen, die von den Multiplikationsoperatoren ausgeführt werden, keine Überlauf- oder Unterlaufbedingungen vorsehen, gehen Informationen möglicherweise verloren, wenn das Ergebnis eines Multiplikationsvorgangs nach der Konvertierung nicht im Typ der Operanden dargestellt werden kann.

Die multiplikativen C-Operatoren sind im Folgenden beschrieben:

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|<strong>\*</strong>|Der multiplikative C-Operator bewirkt die Multiplizierung seiner beiden Operanden.|
|**/**|Der Divisionsoperator bewirkt, dass der erste Operanden durch den zweiten geteilt wird. Wenn zwei ganzzahlige Operanden dividiert werden und das Ergebnis keine ganze Zahl ist, wird sie gemäß den folgenden Regeln gekürzt:<br/><br/>– Das Ergebnis der Division durch 0 (null) ist entsprechend dem ANSI C-Standard nicht definiert. Der Microsoft C-Compiler generiert einen Fehler zur Kompilierzeit oder Laufzeit.<br/><br/>– Wenn beide Operanden positiv oder ohne Vorzeichen sind, wird das Ergebnis in Richtung 0 (null) abgeschnitten.<br/><br/>– Wenn einer der beiden Operanden negativ ist, ist es von der Implementierung abhängig, ob das Ergebnis der Operation die größte ganze Zahl kleiner oder gleich dem algebraischen Quotienten oder die kleinste ganze Zahl größer oder gleich dem algebraischen Quotienten ist. (Siehe den Microsoft-spezifischen Abschnitt unten.)|
|**%**|Das Ergebnis des Restoperators ist das Restergebnis, nachdem der erste Operand durch den zweiten Operanden geteilt wurde. Wenn die Division ungenau ist, wird das Ergebnis durch die folgenden Regeln bestimmt:<br/><br/>– Wenn der rechte Operand 0 (null) ist, ist das Ergebnis nicht definiert.<br/><br/>– Wenn beide Operanden positiv oder ohne Vorzeichen sind, ist das Ergebnis positiv.<br/><br/>– Wenn einer der beiden Operanden negativ und das Ergebnis ungenau ist, ist das Ergebnis von der Implementierung abhängig. (Siehe den Microsoft-spezifischen Abschnitt unten.)|

### <a name="microsoft-specific"></a>Microsoft-spezifisch

In der Division, in der jeder Operand negativ ist, wird in Richtung 0 abgeschnitten.

Wenn eine Division mit dem Restoperator negativ ist, hat das Ergebnis dasselbe Vorzeichen wie der Dividend (der erste Operand im Ausdruck).

## <a name="examples"></a>Beispiele

Die Deklarationen, die unten dargestellt werden, werden für die folgenden Beispiele verwendet:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Diese Anweisung verwendet den Multiplikationsoperator:

```
y = x * i;
```

In diesem Fall wird `x` mit `i` multipliziert, um den Wert 20.0 zu erhalten. Das Ergebnis ist vom Typ **double**.

```
n = i / j;
```

In diesem Beispiel wird 10 durch 3 geteilt. Das Ergebnis wird in Richtung 0 verkürzt, was den Ganzzahlwert 3 liefert.

```
n = i % j;
```

Diese Anweisung weist `n` den ganzzahligen Rest 1 zu, wenn 10 durch 3 dividiert wird.

**Microsoft Specific**

Das Zeichen für den Rest entspricht dem Zeichen des Divisors. Beispiel:

```
50 % -6 = 2
-50 % 6 = -2
```

In jedem Fall haben `50` und `2` dasselbe Zeichen.

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Multiplikativoperatoren und der Modulus-Operator](../cpp/multiplicative-operators-and-the-modulus-operator.md)
