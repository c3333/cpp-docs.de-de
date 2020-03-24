---
title: IEEE-Gleitkommadarstellung
ms.date: 05/06/2019
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
ms.openlocfilehash: bb8523256c05479b303dec66ca79caa28e7cda03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169811"
---
# <a name="ieee-floating-point-representation"></a>IEEE-Gleitkommadarstellung

Microsoft C++ (MSVC) ist mit den numerischen IEEE-Standards konsistent. Der IEEE-754-Standard beschreibt Gleit Komma Formate, eine Möglichkeit zur Darstellung von reellen Zahlen in der Hardware. Es gibt mindestens fünf interne Formate für Gleit Komma Zahlen, die auf der vom MSVC-Compiler vorgesehenen Hardware darstellbar sind, der Compiler verwendet jedoch nur zwei davon. Die Formate mit einfacher *Genauigkeit* (4 Byte) und mit *doppelter Genauigkeit* (8 Byte) werden in MSVC verwendet. Die einfache Genauigkeit wird mithilfe des Schlüssel Worts **float**deklariert. Doppelte Genauigkeit wird mithilfe des Schlüssel Worts **Double**deklariert. Der IEEE-Standard gibt auch die Formate *halbgenauigkeit* (2 Byte) und *vierfache Genauigkeit* (16 Byte) sowie ein Format mit *doppelter* Genauigkeit (10 Byte) an, das einige C-und C++ Compiler als **long Double** -Datentyp implementieren. Im MSVC-Compiler wird der **long Double** -Datentyp als eindeutiger Typ behandelt, aber der Speichertyp ist **Double**zugeordnet. Es gibt jedoch Unterstützung für systeminterne und Assemblysprachen für Berechnungen mit den anderen Formaten, einschließlich des 10-Byte-Formats (Double-Extended-Precision), das von der Hardware unterstützt wird.

Die Werte werden wie folgt gespeichert:

|value|Gespeichert als|
|-----------|---------------|
|Einfache Genauigkeit|Signier Bit, 8-Bit-Exponent, 23-Bit-signifikanor|
|doppelte Genauigkeit|Signier Bit, 11-Bit-Exponent, 52-Bit-signifikanand|
|doppelte Erweiterte Genauigkeit|Signier Bit, 15-Bit-Exponent, 64-Bit-signifikanand|

Bei Formaten mit einfacher Genauigkeit und doppelter Genauigkeit gibt es einen angenommenen führenden 1 im Bruch Teil, der als *signifikanand* (und manchmal auch als *Mantisse*bezeichnet) bezeichnet wird, der nicht im Arbeitsspeicher gespeichert ist, sodass die signifianden tatsächlich 24 oder 53 Bits sind, auch wenn nur 23 oder 52 Bits gespeichert werden. Das Format für die doppelte Erweiterte Genauigkeit speichert dieses Bit tatsächlich.

Die Exponenten sind von der Hälfte ihres möglichen Werts verzerrt. Dies bedeutet, dass Sie diese Abweichung vom gespeicherten Exponent subtrahieren, um den eigentlichen Exponent zu erhalten. Wenn der gespeicherte Exponent kleiner ist als der Bias, ist er tatsächlich ein negativer Exponent.

Die Exponenten sind wie folgt verzerrt:

|Exponent|Verzerrt von|
|--------------|---------------|
|8-Bit (einfache Genauigkeit)|127|
|11-Bit (doppelte Genauigkeit)|1023|
|15-Bit (doppelte Erweiterte Genauigkeit)|16383|

Diese Exponenten sind keine Kräfte von zehn. Dabei handelt es sich um die beiden Kräfte. Das heißt, die gespeicherten 8-Bit-Exponenten können zwischen-127 und 127 liegen, die als 0 bis 254 gespeichert werden. Der Wert 2<sup>127</sup> entspricht ungefähr 10<sup>38</sup>. Dies ist der tatsächliche Grenzwert für die einfache Genauigkeit.

Der signifiund wird als binärer Bruchteil der Form 1.xxx... gespeichert. Dieser Bruchteil hat einen Wert größer oder gleich 1 und kleiner als 2. Beachten Sie, dass reelle Zahlen immer in *normalisierter Form*gespeichert werden. Das heißt, der signifikanand wird nach links verschoben, sodass das höchst wertige Bit von signifikanund immer 1 ist. Da dieses Bit immer 1 ist, wird es in den Formaten mit einfacher Genauigkeit und mit doppelter Genauigkeit angenommen (nicht gespeichert). Es wird davon ausgegangen, dass der binäre (nicht dezimal-) Punkt direkt rechts von der führenden 1 liegt.

Das Format für die verschiedenen Größen lautet dann wie folgt:

|Format|Byte 1|Byte 2|Byte 3|Byte 4|...|Byte n|
|------------|------------|------------|------------|------------|---------|------------|
|Einfache Genauigkeit| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|doppelte Genauigkeit|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|doppelte Erweiterte Genauigkeit|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` das das Signier Bit darstellt, sind die `X`die unausgewogenen Exponentenbits, und die `M`sind die signifikanten und Bits. Beachten Sie, dass das ganz linke Bit in Formaten mit einfacher Genauigkeit und doppelter Genauigkeit angenommen wird, aber in Byte 3 des Formats mit doppelter Genauigkeit als "1" vorhanden ist.

Um den Binär Punkt ordnungsgemäß zu verschieben, entfernen Sie zuerst den Exponenten, und verschieben Sie dann den Binär Punkt nach rechts, oder lassen Sie die entsprechende Anzahl von Bits zurück.

## <a name="special-values"></a>Besondere Werte

Die Gleit Komma Formate enthalten einige Werte, die speziell behandelt werden.

### <a name="zero"></a>Null

NULL kann nicht normalisiert werden, wodurch Sie in der normalisierten Form eines Werts mit einfacher Genauigkeit oder doppelter Genauigkeit nicht dargestellt werden kann. Ein spezielles Bitmuster aller Nullen stellt 0 dar. Es ist auch möglich,-0 als 0 (null) anzugeben, wenn das Signier Bit festgelegt ist, aber-0 und 0 vergleichen immer gleich.

### <a name="infinities"></a>Unendlichkeiten

Die Werte "+" und "-" werden durch einen Exponenten aller Werte und ein signifiund aller Nullen dargestellt. Positive und negative Unendlichkeiten können mithilfe des Signier Bits dargestellt werden.

### <a name="subnormals"></a>Subnormale

Es ist möglich, Zahlen kleiner als die kleinste normalisierte Zahl darzustellen. Diese Zahlen werden als *subnormale* oder *denormale* Zahlen bezeichnet. Wenn der Exponent aus Nullen besteht und der Wert ungleich 0 (null) ist, wird das implizite vorangehende Bit des signifikanals als 0 (null) betrachtet, nicht als eins. Die Genauigkeit der subnormalen Zahlen sinkt als Anzahl der führenden Nullen im signifizierer und steigt.

### <a name="nan---not-a-number"></a>Nan-not a Number

Werte, die keine reelle Zahl sind, wie z. b. 0/0, können im IEEE-Gleit Komma Format dargestellt werden. Ein Wert dieser Art wird als *NaN*bezeichnet. Ein NaN wird durch einen Exponenten aller Werte und ein signifikanungleich NULL dargestellt. Es gibt zwei Arten von Nane, *quiet* Nane oder qnane und *signalisiert* Nane oder snane. Quiet Nane haben einen führenden im signifiund und werden im Allgemeinen durch einen Ausdruck weitergegeben. Sie stellen einen unbestimmten Wert dar, z. b. das Ergebnis der Division durch unendlich oder das Multiplizieren von unendlich um NULL. die Signalisierung der Nane hat eine führende Null. Diese werden für Vorgänge verwendet, die nicht gültig sind, um eine Gleit Komma-Hardware Ausnahme zu signalisieren.

## <a name="examples"></a>Beispiele

Im folgenden finden Sie einige Beispiele im Format mit einfacher Genauigkeit:

- Für den Wert 2 ist das Signier Bit 0 (null), und der gespeicherte Exponent ist 128 oder 1000 0000 in binary (127 Plus 1). Das gespeicherte binäre signifiund ist (1.) 000 0000 0000 0000 0000 0000, das über einen impliziten führenden 1-und binärpunkt verfügt, d. h., der tatsächliche signifiund ist ein Wert.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Der Wert-2. Identisch mit + 2 mit der Ausnahme, dass das Signier Bit festgelegt ist. Dies gilt für den negativen Wert aller Gleit Komma Zahlen im IEEE-Format.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Der Wert 4. Der gleiche signifiund der Exponent erhöht sich um eins (der unausgewogene Wert ist 129 oder 100 0000 1 in Binary.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Der Wert 6. Der gleiche Exponent, signifiund ist größer als die Hälfte – er ist (1.) 100 0000... 0000 0000, da es sich um einen binären Bruchteil handelt, ist 1 1/2, weil die Werte der Dezimalstellen 1/2, 1/4, 1/8 usw. sind.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |6|1,5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Der Wert 1. Die gleiche signifiprise und die anderen Potenzen von zwei, der unausgewogene Exponent ist ein kleiner als 2 um 127, oder 011 1111 1 in Binary.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Der Wert 0,75. Der unausgewogene Exponent ist 126, 011 1111 0 in binary, und der signifiand ist (1.) 100 0000... 0000 0000, 1 1/2.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0.75|1,5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Der Wert 2,5. Genau identisch mit zwei, außer dass das Bit, das 1/4 darstellt, im signifiund festgelegt wird.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |2.5|1,25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 ist ein wiederholter Bruchteil in der Binärdatei. Der signifiand ist nur ein gewisser Wert von 1,6, und der dezimale Exponent besagt, dass 1,6 durch 16 dividiert werden muss (es ist 011 1101 1 in binary, die 123 in Decimal ist). Der wahre Exponent ist 123-127 =-4. Dies bedeutet, dass der Faktor, um den multipliziert werden soll, 2<sup>-4</sup> = 1/16 ist. Beachten Sie, dass das gespeicherte signifiund im letzten Bit aufgerundet werden – ein Versuch, die nicht darstellbare Zahl so genau wie möglich darzustellen. (Der Grund, warum 1/10 und 1/100 in Binärdateien nicht genau darstellbar sind, ähnelt dem Grund, warum 1/3 nicht genau in Dezimalform dargestellt werden kann.)

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0,1|1,6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3dcccccd|

- NULL ist ein Sonderfall, der die Formel für den minimal möglichen darstellbaren positiven Wert verwendet, bei dem es sich um Nullen handelt.

   |value|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Weitere Informationen

[Warum Gleitkommazahlen an Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md)
