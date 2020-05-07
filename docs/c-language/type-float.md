---
title: Typ "float"
ms.date: 11/04/2016
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
ms.openlocfilehash: 61bfd094801165e0c3e41e5de6fcbfb0c5e59504
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346326"
---
# <a name="type-float"></a>Typ "float"

Gleitkommazahlen verwenden das IEEE(Institute of Electrical and Electronics Engineers)-Format. Werte mit einfacher Genauigkeit vom Typ "float" umfassen 4 Bytes und bestehen aus einem Vorzeichenbit, einem 8-Bit-Exponenten in Excess-127-Notation und einer 23-Bit-Mantisse. Die Mantisse ist eine Zahl zwischen 1.0 und 2.0. Da das höchstwertige Bit der Mantisse immer 1 ist, wird es nicht in der Zahl gespeichert. Diese Darstellung erlaubt einen Bereich von etwa 3,4E-38 bis 3,4E+38 für den Typ „float“.

Sie können Variablen als "float" oder "double" deklarieren, abhängig von den Anforderungen der Anwendung. Die wichtigsten Unterschiede zwischen den beiden Typen sind die darstellbare Signifikanz, der benötigte Speicher und der Gültigkeitsbereich. Die folgende Tabelle zeigt die Beziehung zwischen Signifikanz und Speicheranforderungen.

### <a name="floating-point-types"></a>Gleitkommatypen

|Typ|Signifikante Stellen|Anzahl von Bytes|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Gleitkommavariablen werden von einer Mantisse, die den Wert der Zahl enthält, und einem Exponenten dargestellt, der die Größenordnung der Zahl enthält.

Die folgende Tabelle zeigt die Anzahl von Bits, die der Mantisse und dem Exponenten für den jeweiligen Gleitkommatyp zugewiesen werden. Das höchstwertige Bit von "float" oder "double" ist das Vorzeichenbit. Wenn es 1 ist, gilt die Zahl als negativ, andernfalls als eine positive Zahl.

### <a name="lengths-of-exponents-and-mantissas"></a>Längen der Exponenten und Mantissen

|Typ|Exponentenlänge|Mantissenlänge|
|----------|---------------------|---------------------|
|float|8 Bit|23 Bit|
|double|11 Bit|52 Bit|

Da Exponenten in der Form ohne Vorzeichen gespeichert werden, werden die Exponenten mit der Hälfte ihres möglichen Werts gewichtet. Für den Typ "float" ist die Gewichtung 127, für "double" ist es 1.023. Sie können den tatsächlichen Wert für den Exponenten berechnen, indem die Gewichtung vom Exponenten subtrahiert wird.

Die Mantisse wird als Binärbruch größer oder gleich 1 und kleiner als 2 gespeichert. Für die Typen "float" und "double" gibt es eine implizite führende 1 in der Mantisse an der Position des höchstwertigen Bits, sodass die Mantissen eigentlich 24 bzw. 53 Bits lang sind, obwohl das höchstwertige Byte nie im Arbeitsspeicher gespeichert ist.

Anstelle der gerade beschriebenen Speichermethode kann das Gleitkommapaket binäre Gleitkommazahlen als denormalisierte Zahlen speichern. "Denormalisierte Zahlen" sind Gleitkommazahlen ungleich 0 (null) mit reservierten Exponentenwerten, in denen das höchstwertige Bit der Mantisse 0 ist. Durch Verwendung des denormalisierten Formats, kann der Gültigkeitsbereich einer Gleitkommazahl auf Kosten der Genauigkeit erweitert werden. Sie können nicht steuern, ob eine Gleitkommazahl in der normalisierten oder denormalisierten Form dargestellt wird. Das Gleitkommapaket bestimmt die Darstellung. Das Gleitkommapaket verwendet nie eine denormalisierte Form, es sei denn der Exponent wird niedriger als das Minimum, das in normalisierter Form dargestellt werden kann.

Die folgende Tabelle zeigt die Minimal- und Maximalwerte, die Sie in Variablen für den jeweiligen Gleitkommatyp speichern können. Die Werte, die in dieser Tabelle aufgeführt sind, gelten nur für normalisierte Gleitkommazahlen. Denormalisierte Gleitkommazahlen haben einen kleineren minimalen Wert. Beachten Sie, dass die Zahlen, die in 80*x*87-Registern beibehalten werden, immer in normalisierter Form von 80 Bit dargestellt werden. Zahlen können nur in denormalisierter Form dargestellt werden, wenn sie in 32-Bit- oder 64-Bit-Gleitkommavariablen (Variablen vom Typ „float“ und Typ „long“) gespeichert werden.

### <a name="range-of-floating-point-types"></a>Bereiche von Gleitkommatypen

|Typ|Minimalwert|Maximalwert|
|----------|-------------------|-------------------|
|frei verschieben|1,175494351 E - 38|3.402823466 E + 38|
|double|2,2250738585072014 E - 308|1,7976931348623158 E + 308|

Wenn Genauigkeit weniger wichtig ist als Speicherbelegung, sollten Sie für Gleitkommavariablen den float-Typ verwenden. Wenn Genauigkeit das wichtigste Kriterium ist, verwenden Sie den double-Typ.

Gleitkommavariablen können in einen Typ mit größerer Signifikanz heraufgestuft werden (vom Typ "float" in den Typ "double"). Die Heraufstufung tritt häufig auf, wenn Sie Arithmetik für Gleitkommavariablen ausführen. Diese Arithmetik wird immer mit derselben Genauigkeit durchgeführt, den die Variable mit dem höchsten Grad an Genauigkeit aufweist. Betrachten Sie beispielsweise die folgenden Typdeklarationen:

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

Im vorhergehenden Beispiel wird die Variable `f_short` in den Typ "double" heraufgestuft und mit `f_long` multipliziert. Anschließend wird das Ergebnis in den Typ "float" gerundet, bevor es `f_short` zugewiesen wird.

Im folgenden Beispiel (das die Deklarationen aus dem vorherigen Beispiel verwendet), wird die Arithmetik mit float-Genauigkeit (32-Bit) für die Variablen ausgeführt. Anschließend wird das Ergebnis in den Typ "double" heraufgestuft:

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Siehe auch

[Speicherung von einfachen Typen](../c-language/storage-of-basic-types.md)
