---
title: Konvertierungen von Gleitkommatypen
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998714"
---
# <a name="conversions-from-floating-point-types"></a>Konvertierungen von Gleitkommatypen

Ein Gleitkommawert, der in einen anderen Gleitkommatyp konvertiert wird, wird nicht geändert, wenn der ursprüngliche Wert exakt im Ergebnistyp dargestellt werden kann. Wenn der ursprüngliche Wert numerisch ist, aber nicht exakt dargestellt werden kann, ist das Ergebnis entweder der nächste höhere oder nächste niedrigere darstellbare Wert. Weitere Informationen über den Bereich von Gleitkommatypen erhalten Sie unter [Grenzwerte für Gleitkommakonstanten](../c-language/limits-on-floating-point-constants.md).

Ein Gleitkommawert, der in einen integralen Typ konvertiert wird, wird zunächst abgeschnitten, indem etwaige Bruchwerte verworfen werden. Wenn dieser gekürzte Wert im Ergebnistyp darstellbar ist, muss das Ergebnis dieser Wert sein. Wenn er nicht darstellbar ist, ist der Ergebniswert nicht definiert.

**Microsoft-spezifisch**

Microsoft-Compiler verwenden die IEEE-754-Binär32-Darstellung für **float**-Werte und die Binär64-Darstellung für **long double**- und **double**-Werte. Da **long double** und **double** dieselbe Darstellung verwenden, weisen sie denselben Bereich und dieselbe Genauigkeit auf.

Wenn der Compiler eine **double**- oder **long double**-Gleitkommazahl in einen **float**-Wert konvertiert, wird das Ergebnis gemäß der Umgebungssteuerung für Gleitkommazahlen gerundet, die standardmäßig „auf Nächste runden, an Gerade binden“ ist. Wenn ein numerischer Wert zu hoch oder zu niedrig ist, um als numerischer **float**-Wert dargestellt zu werden, ist das Konvertierungsergebnis entsprechend dem Vorzeichen des ursprünglichen Werts positiv oder negativ unendlich, und es wird eine Überlaufausnahme ausgelöst, falls aktiviert.

Bei der Konvertierung in ganzzahlige Typen ist das Ergebnis einer Konvertierung in einen Typ kleiner als **long** das Ergebnis der Konvertierung des Werts in **long** und der anschließenden Konvertierung in den Ergebnistyp.

Bei der Konvertierung in ganzzahlige Typen, die mindestens so groß wie **long** sind, kann eine Konvertierung eines Werts, der zu hoch oder zu niedrig ist, um im Ergebnistyp dargestellt zu werden, jeden der folgenden Werte zurückgeben:

- Das Ergebnis kann ein *Sentinelwert* sein, bei dem es sich um den darstellbaren Wert von 0 (null) handelt. Bei signierten Typen ist dies der niedrigste darstellbare Wert (0x800... 0). Bei nicht signierten Typen ist dies der höchste darstellbare Wert (0xFF...F).

- Das Ergebnis kann *gesättigt* sein, wobei Werte, die zu hoch sind, um dargestellt zu werden, in den höchsten darstellbaren Wert und Werte, die zu niedrig sind, um dargestellt zu werden, in den niedrigsten darstellbaren Wert konvertiert werden. Einer dieser beiden Werte wird auch als Sentinelwert verwendet.

- Bei der Konvertierung in **unsigned long** oder **unsigned long long** kann das Ergebnis der Konvertierung eines Werts außerhalb des Bereichs ein anderer Wert als der höchste oder niedrigste darstellbare Wert sein. Ob das Ergebnis ein Sentinelwert oder ein gesättigter Wert ist, hängt von den Compileroptionen und der Zielarchitektur ab. Zukünftige Compilerreleases können stattdessen einen gesättigten Wert oder einen Sentinelwert zurückgeben.

**Ende Microsoft-spezifisch**

In der folgenden Tabelle werden die Konvertierungen von Gleitkommatypen zusammengefasst.

## <a name="table-of-conversions-from-floating-point-types"></a>Tabelle für Konvertierungen von Gleitkommatypen

|Von|Beschreibung|Methode|
|----------|--------|------------|
|**float**|**char**|Konvertieren in **long**; Konvertieren von **long** in **char**|
|**float**|**short**|Konvertieren in **long**; Konvertieren von **long** in **short**|
|**float**|**int**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **int** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**langes long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **long long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**unsigned char**|Konvertieren in **long**; Konvertieren von **long** in **unsigned char**|
|**float**|**unsigned short**|Konvertieren in **long**; Konvertieren von **long** in **unsigned short**|
|**float**|**unsigned**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**unsigned long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**unsigned long long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned long long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**float**|**double**|Darstellen als **double**.|
|**float**|**long double**|Darstellen als **long double**.|
|**double**|**char**|Konvertieren in **float**; Konvertieren von **float** in **char**|
|**double**|**short**|Konvertieren in **float**; Konvertieren von **float** in **short**|
|**double**|**int**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **int** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**unsigned char**|Konvertieren in **long**; Konvertieren von **long** in **unsigned char**|
|**double**|**unsigned short**|Konvertieren in **long**; Konvertieren von **long** in **unsigned short**|
|**double**|**unsigned**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**unsigned long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**unsigned long long**|Beim Dezimaltrennzeichen abschneiden. Wenn das Ergebnis zu groß ist, um als **unsigned long long** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**float**|Darstellen als **float**. Wenn ein **double**-Wert nicht exakt als **float** dargestellt werden kann, tritt ein Genauigkeitsverlust auf. Wenn der Wert zu groß ist, um als **float** dargestellt zu werden, ist das Ergebnis nicht definiert.|
|**double**|**long double**|Der Wert **long double** wird als **double** behandelt.|

Konvertierungen von **long double** folgen derselben Methode wie Konvertierungen von **double**.

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
