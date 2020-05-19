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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169811"
---
# <a name="ieee-floating-point-representation"></a>IEEE-Gleitkommadarstellung

Microsoft C++ (MSVC) erfüllt die numerischen IEEE-Standards. Der IEEE-754-Standard beschreibt Gleitkommaformate. Gleitkommazahlen sind eine Art, reelle Zahlen in der Hardware darzustellen. Es gibt mindestens fünf interne Formate für Gleitkommazahlen, die in der Hardware darstellbar sind, für die der MSVC-Compiler kompiliert. Der Compiler verwendet jedoch nur zwei davon. In MSVC werden die Formate mit *einfacher* (4 Byte) und *doppelter Genauigkeit* (8 Byte) verwendet. Das Format mit einfacher Genauigkeit wird mithilfe des Schlüsselworts **float** deklariert. Das Format mit doppelter Genauigkeit wird mithilfe des Schlüsselworts **double** deklariert. Der IEEE-Standard sieht ebenfalls ein Format mit *halber Genauigkeit* (2 Byte), ein Format mit *vierfacher Genauigkeit* (16 Byte) sowie ein Format mit *doppelt erweiterter Genauigkeit* (10 Byte) vor. Letzteres wird von einigen C- und C++-Compilern als **long double**-Datentyp implementiert. Im MSVC-Compiler wird der Datentyp **long double** zwar dem Speichertyp **double** zugeordnet, jedoch als ein anderer Datentyp verarbeitet. Berechnungen, in denen andere Formate wie das mit doppelt erweiterter Genauigkeit (10 Byte) verwendet werden, werden sowohl intrinsisch als auch von der Assemblysprache unterstützt. Voraussetzung dafür ist, dass solche Berechnungen überhaupt von der Hardware unterstützt werden.

Die Werte werden wie folgt gespeichert:

|Wert|Gespeichert als|
|-----------|---------------|
|Einfache Genauigkeit|Vorzeichenbit, 8-Bit-Exponent, 23-Bit-Mantisse|
|Gleitkommawert mit doppelter Genauigkeit|Vorzeichenbit, 11-Bit-Exponent, 52-Bit-Mantisse|
|Doppelt erweiterte Genauigkeit|Vorzeichenbit, 15-Bit-Exponent, 64-Bit-Mantisse|

Bei Formaten mit einfacher und doppelter Genauigkeit wird in der *Mantisse* eine führende 1 angenommen, die nicht im Arbeitsspeicher gespeichert wird. Die *Mantisse* enthält also tatsächlich 24 bzw. 53 Bits, selbst wenn nur 23 bzw. 52 Bits gespeichert werden. Im Format mit doppelt erweiterter Genauigkeit wird dieses Bit tatsächlich gespeichert.

Die Exponenten werden um die Hälfte ihres möglichen Werts zur Null verschoben (Bias). Dies bedeutet, dass Sie diesen Bias vom gespeicherten Exponenten subtrahieren müssen, um den tatsächlichen Exponenten zu erhalten. Wenn der gespeicherte Exponent kleiner ist als der Bias, handelt es sich um einen negativen Exponenten.

Die Exponenten werden wie folgt zur Null verschoben:

|Exponent|Verschoben um|
|--------------|---------------|
|8 Bit (einfache Genauigkeit)|127|
|11 Bit (doppelte Genauigkeit)|1023|
|15 Bit (doppelt erweiterte Genauigkeit)|16383|

Diese Exponenten sind keine Potenzen von 10, sondern von 2. Das heißt, die gespeicherten 8-Bit-Exponenten von –127 bis 127 reichen können und als eine Zahl von 0 bis 254 gespeichert werden. Der Wert 2<sup>127</sup> entspricht ungefähr 10<sup>38</sup>. Dies ist der tatsächliche Grenzwert für Werte mit einfacher Genauigkeit.

Die Mantisse wird als binärer Bruch der Form 1.xxx... gespeichert. Dieser Bruch ist größer als oder gleich 1 und kleiner als 2. Beachten Sie, dass reelle Zahlen immer in *normalisierter Form gespeichert werden*. Das heißt, dass die Mantisse nach links verschoben wird, sodass das höchstwertige Bit der Mantisse immer 1 ist. Da dieses Bit immer 1 ist, wird es in den Formaten mit einfacher und doppelter Genauigkeit immer angenommen (nie gespeichert). Es wird davon ausgegangen, dass der Binärpunkt (nicht das Dezimalkomma) gleich rechts der führenden 1 steht.

Das Format für die verschiedenen Größen lautet dann wie folgt:

|Format|Byte 1|Byte 2|Byte 3|Byte 4|...|Byte n|
|------------|------------|------------|------------|------------|---------|------------|
|Einfache Genauigkeit| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|Doppelte Genauigkeit|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|Doppelt erweiterte Genauigkeit|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` stellt das Vorzeichenbit dar. Jedes `X` steht für ein verschobenes Exponentenbit, und jedes `M` ist ein Mantissenbit. Beachten Sie, dass das äußerste linke Bit im Format mit einfacher und doppelter Genauigkeit nur angenommen wird, während die 1 in Byte 3 im Format mit doppelt erweiterter Genauigkeit explizit vorhanden ist.

Für das korrekte Verschieben des Binärpunkts müssen Sie zuerst die Verschiebung des Exponenten aufheben und den Binärpunkt anschließend um die korrekte Anzahl von Bits nach rechts oder links verschieben.

## <a name="special-values"></a>Besondere Werte

Die Gleitkommaformate enthalten einige Werte, die anders als andere behandelt werden.

### <a name="zero"></a>Zero

Null kann nicht normalisiert und damit auch nicht in der normalisierten Form eines Werts mit einfacher oder doppelter Genauigkeit dargestellt werden. 0 wird durch ein spezielles Bitmuster dargestellt, das ausschließlich Nullen enthält. Es ist auch möglich, –0 als Null mit einem Vorzeichenbit darzustellen. –0 und 0 gelten jedoch immer als gleich.

### <a name="infinities"></a>Unendlichkeiten

Die Werte +∞ und −∞ werden durch einen Exponenten aus reinen Nullen und eine Mantisse aus reinen Einsen dargestellt. Positive und negative Unendlichkeiten können mithilfe des Vorzeichenbits dargestellt werden.

### <a name="subnormals"></a>Denormalisierte Zahlen

Es ist möglich, Zahlen darzustellen, die kleiner als die kleinste normalisierte Zahl sind. Diese Zahlen werden auch als *subnormale* oder *denormalisierte* Zahlen bezeichnet. Wenn der Exponent aus Nullen besteht und die Mantisse ungleich 0 ist, wird das implizite vorangehende Bit der Mantisse als 0 angesehen, nicht als 1. Die Genauigkeit von denormalisierten Zahlen sinkt, je höher die Anzahl der führenden Nullen in der Mantisse ist.

### <a name="nan---not-a-number"></a>NaN (Not a Number, keine Zahl)

Im IEEE-Gleitkommaformat lassen sich auch Werte darstellen, die keine reelle Zahl sind, z. B. 0/0. Ein solcher Wert wird als *NaN* bezeichnet. Ein NaN-Wert wird durch einen Exponenten, der nur Einsen enthält, und eine Mantisse dargestellt, die ungleich Null ist. Es gibt zwei Arten von NaNs: *stille* NaNs (quiet NaNs, QNaNs) und *signalisierende* NaNs (signaling NaNs, SNaNs). Bei stillen NaNs wird die Mantisse durch eine 1 angeführt. Außerdem werden stille NaNs im Allgemeinen innerhalb eines Ausdrucks immer weitergegeben. Sie stellen einen unbestimmten Wert dar, z. B. das Ergebnis der Division durch unendlich oder das Ergebnis der Multiplikation von unendlich mal Null. Signalisierende NaNs weisen eine führende Null in der Mantisse auf. Sie werden für Vorgänge verwendet, die nicht gültig sind, um eine Gleitkomma-Hardwareausnahme zu signalisieren.

## <a name="examples"></a>Beispiele

Im Folgenden finden Sie einige Beispiele im Format mit einfacher Genauigkeit:

- Für den Wert 2 ist das Vorzeichenbit 0, und der gespeicherte Exponent lautet 128 oder 1000 0000 als Binärzahl (Ergebnis von 127+1). Die gespeicherte binäre Mantisse lautet (1.). 000 0000 0000 0000 0000 0000. Da sie über eine implizite führende 1 und einen Binärpunkt verfügt, lautet die tatsächliche Mantisse 1.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |2|1 x 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Der Wert –2. Genauso wie +2, nur dass das Vorzeichenbit festgelegt ist. Dies gilt für die negativen Werte aller Gleitkommazahlen im IEEE-Format.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |-2|–1 x 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Der Wert 4. Dieselbe Mantisse, der Exponent erhöht sich um 1. Der zu Null verschobene Wert ist 129 oder 100 0000 1 (Binärzahl).

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |4|1 x 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Der Wert 6. Derselbe Exponent. Die Mantisse wurde um die Hälfte vergrößert und lautet (1). 100 0000 ... 0000 0000. Dies ist gleich 1 1/2, da es sich um einen binären Bruch handelt und die Werte der Dezimalstellen 1/2, 1/4, 1/8 usw. sind.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |6|1,5 x 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Der Wert 1. Dieselbe Mantisse wie andere Potenzen von Zwei. Der zur Null verschobene Exponent ist um 1 kleiner als der des Werts 2 bei 127, oder 011 1111 1 im Binärformat.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |1|1 x 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Der Wert 0,75. Der zur Null verschobene Exponent ist 126, 011 1111 0 (Binärzahl), und die Mantisse ist (1.) 100 0000 ... 0000 0000, was 1 1/2 ist.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0.75|1,5 x 2<sup>–1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Der Wert 2,5: Genau identisch mit Zwei, außer dass das Bit, das 1/4 darstellt, in der Mantisse festgelegt wird.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |2.5|1,25 x 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 ist ein sich wiederholter Bruch im Binärformat. Die Mantisse liegt knapp unterhalb von 1,6, und der zur Null verschobene Exponent besagt, dass 1,6 durch 16 dividiert werden muss (011 1101 1 im Binärformat, was 123 im Dezimalformat entspricht). Der wahre Exponent ist 123–127=4, was bedeutet, das der Faktor, mit dem multipliziert werden muss, 2<sup>–4</sup>=1/16 ist. Beachten Sie, dass die gespeicherte Mantisse im letzten Bit aufgerundet wird. Dies ist ein Versuch, die nicht darstellbare Zahl so genau wie möglich darzustellen. (Der Grund, warum 1/10 und 1/100 im Binärformat nicht genau darstellbar sind, ähnelt dem Grund, warum 1/3 nicht genau in Dezimalform dargestellt werden kann.)

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0.1|1,6 x 2<sup>–4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Null ist ein Sonderfall, in dem die Formel für den minimal möglichen darstellbaren positiven Wert verwendet wird. Dabei handelt es sich um einen Wert, der nur aus Nullen besteht.

   |Wert|Formel|Binäre Darstellung|Hexadezimal|
   |-|-|-|-|
   |0|1 x 2<sup>–128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Siehe auch

[Warum Gleitkommazahlen an Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md)
