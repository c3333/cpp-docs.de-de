---
title: Konvertierungen von Gleitkommatypen
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: 72d0f95a6e48dcf0a5e8fea3757e85f9a03bf7e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227893"
---
# <a name="conversions-from-floating-point-types"></a>Konvertierungen von Gleitkommatypen

Ein Gleitkommawert, der in einen anderen Gleitkommatyp konvertiert wird, wird nicht geändert, wenn der ursprüngliche Wert exakt im Ergebnistyp dargestellt werden kann. Wenn der ursprüngliche Wert numerisch ist, aber nicht exakt dargestellt werden kann, ist das Ergebnis entweder der nächste höhere oder nächste niedrigere darstellbare Wert. Weitere Informationen über den Bereich von Gleitkommatypen erhalten Sie unter [Grenzwerte für Gleitkommakonstanten](../c-language/limits-on-floating-point-constants.md).

Ein Gleitkommawert, der in einen integralen Typ konvertiert wird, wird zunächst abgeschnitten, indem etwaige Bruchwerte verworfen werden. Wenn dieser gekürzte Wert im Ergebnistyp darstellbar ist, muss das Ergebnis dieser Wert sein. Wenn er nicht darstellbar ist, ist der Ergebniswert nicht definiert.

**Microsoft-spezifisch**

Microsoft-Compiler verwenden die 32-Bit-IEEE-754-Binärdarstellung für **`float`** -Werte und die 64-Bit-Binärdarstellung für **`long double`** - und **`double`** -Werte. Da **`long double`** und **`double`** dieselbe Darstellung verwenden, weisen sie denselben Bereich und dieselbe Genauigkeit auf.

Wenn der Compiler eine **`double`** - oder **`long double`** -Gleitkommazahl in einen **`float`** -Wert konvertiert, wird das Ergebnis gemäß der Umgebungssteuerung für Gleitkommazahlen standardmäßig auf die nächste gerade Zahl gerundet. Wenn ein numerischer Wert zu hoch oder zu niedrig ist, um als numerischer **`float`** -Wert dargestellt zu werden, ist das Konvertierungsergebnis entsprechend dem Vorzeichen des ursprünglichen Werts positiv oder negativ unendlich, und es wird eine Überlaufausnahme ausgelöst, falls diese aktiviert ist.

Bei der Konvertierung in ganzzahlige Typen entspricht das Ergebnis einer Konvertierung in einen Typ kleiner als **`long`** das Ergebnis der Konvertierung des Werts in **`long`** und der anschließenden Konvertierung in den Ergebnistyp.

Bei der Konvertierung in ganzzahlige Typen, die größer oder gleich **`long`** sind, kann eine Konvertierung eines Werts, der zu hoch oder zu niedrig ist, um im Ergebnistyp dargestellt zu werden, jeden der folgenden Werte zurückgeben:

- Das Ergebnis kann ein *Sentinelwert* sein, bei dem es sich um den darstellbaren Wert von 0 (null) handelt. Bei signierten Typen ist dies der niedrigste darstellbare Wert (0x800... 0). Bei nicht signierten Typen ist dies der höchste darstellbare Wert (0xFF...F).

- Das Ergebnis kann *gesättigt* sein, wobei Werte, die zu hoch sind, um dargestellt zu werden, in den höchsten darstellbaren Wert und Werte, die zu niedrig sind, um dargestellt zu werden, in den niedrigsten darstellbaren Wert konvertiert werden. Einer dieser beiden Werte wird auch als Sentinelwert verwendet.

- Bei der Konvertierung in **`unsigned long`** oder **`unsigned long long`** kann das Ergebnis der Konvertierung eines Werts außerhalb des Bereichs ein anderer Wert als der höchste oder niedrigste darstellbare Wert sein. Ob das Ergebnis ein Sentinelwert oder ein gesättigter Wert ist, hängt von den Compileroptionen und der Zielarchitektur ab. Zukünftige Compilerreleases können stattdessen einen gesättigten Wert oder einen Sentinelwert zurückgeben.

**Ende Microsoft-spezifisch**

In der folgenden Tabelle werden die Konvertierungen von Gleitkommatypen zusammengefasst.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabelle für Konvertierungen von Gleitkommatypen

|Von|Beschreibung|Methode|
|----------|--------|------------|
|**`float`**|**`char`**|In **`long`** konvertieren, **`long`** in **`char`** konvertieren|
|**`float`**|**`short`**|In **`long`** konvertieren, **`long`** in **`short`** konvertieren|
|**`float`**|**`int`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`int`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`long`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`long long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`long long`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`unsigned char`**|In **`long`** konvertieren, **`long`** in **`unsigned char`** konvertieren|
|**`float`**|**`unsigned short`**|In **`long`** konvertieren, **`long`** in **`unsigned short`** konvertieren|
|**`float`**|**`unsigned`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`unsigned long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned long`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`unsigned long long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned long long`** dargestellt zu werden, wird es nicht definiert.|
|**`float`**|**`double`**|Als **`double`** darstellen|
|**`float`**|**`long double`**|Als **`long double`** darstellen|
|**`double`**|**`char`**|In **`float`** konvertieren, **`float`** in **`char`** konvertieren|
|**`double`**|**`short`**|In **`float`** konvertieren, **`float`** in **`short`** konvertieren|
|**`double`**|**`int`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`int`** dargestellt zu werden, wird es nicht definiert.|
|**`double`**|**`long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`long`** dargestellt zu werden, wird es nicht definiert.|
|**`double`**|**`unsigned char`**|In **`long`** konvertieren, **`long`** in **`unsigned char`** konvertieren|
|**`double`**|**`unsigned short`**|In **`long`** konvertieren, **`long`** in **`unsigned short`** konvertieren|
|**`double`**|**`unsigned`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned`** dargestellt zu werden, wird es nicht definiert.|
|**`double`**|**`unsigned long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned long`** dargestellt zu werden, wird es nicht definiert.|
|**`double`**|**`unsigned long long`**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **`unsigned long long`** dargestellt zu werden, wird es nicht definiert.|
|**`double`**|**`float`**|Als **`float`** darstellen Wenn ein **`double`** -Wert nicht exakt als **`float`** dargestellt werden kann, tritt ein Genauigkeitsverlust auf. Wenn der Wert zu groß ist, um als **`float`** dargestellt zu werden, wird das Ergebnis nicht definiert.|
|**`double`**|**`long double`**|Der Wert **`long double`** wird als **`double`** behandelt.|

Bei Konvertierungen von **`long double`** wird das gleiche Verfahren wie bei Konvertierungen von **`double`** angewendet.

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
