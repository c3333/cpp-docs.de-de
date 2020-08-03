---
title: Konvertierungen von integralen Typen ohne Vorzeichen
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 08b88b1343f56f8d79fc39c53505b26caecfe3c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226463"
---
# <a name="conversions-from-unsigned-integral-types"></a>Konvertierungen von integralen Typen ohne Vorzeichen

Wenn eine ganze Zahl ohne Vorzeichen in einen Integer- oder einen Gleitkommatyp konvertiert wird, bleibt der Wert unverändert, falls der ursprüngliche Wert im Ergebnistyp darstellbar ist.

Beim Konvertieren einer ganzen Zahl ohne Vorzeichen in eine größere ganze Zahl konvertiert wird, wird der Wert mit 0 erweitert. Wenn sie in eine kleinere ganze Zahl konvertiert wird, werden die höherwertigen Bits abgeschnitten. Das Ergebnis wird mithilfe des Ergebnistyps wie in diesem Beispiel gezeigt interpretiert.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Beim Konvertieren einer ganzen Zahl ohne Vorzeichen in einen Gleitkommatyp ist das Ergebnis, falls der ursprüngliche Wert nicht genau im Ergebnistyp dargestellt werden kann, der nächsthöhere oder -niedrigere darstellbare Wert.

Informationen über die Größen der Integer- und Gleitkommatypen finden Sie unter [Speicherverwendung der grundlegenden Typen](../c-language/storage-of-basic-types.md).

**Microsoft-spezifisch**

Im Microsoft-Compiler sind die Werte **`unsigned`** (oder **`unsigned int`** ) und **`unsigned long`** eindeutige aber äquivalente Typen. Die Konvertierung eines **`unsigned int`** -Werts wird auf dieselbe Weise wie die Konvertierung eines **`unsigned long`** -Werts ausgeführt.

**Ende Microsoft-spezifisch**

In der folgenden Tabelle werden die Konvertierungen von ganzzahligen Typen ohne Vorzeichen zusammengefasst.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tabelle mit Konvertierungen von integralen Typen ohne Vorzeichen

|Von|Beschreibung|Methode|
|----------|--------|------------|
|**`unsigned char`**|**`char`**|Bitmuster wird beibehalten; oberes Bit wird Vorzeichenbit|
|**`unsigned char`**|**`short`**|Nullerweiterung|
|**`unsigned char`**|**`long`**|Nullerweiterung|
|**`unsigned char`**|**`long long`**|Nullerweiterung|
|**`unsigned char`**|**`unsigned short`**|Nullerweiterung|
|**`unsigned char`**|**`unsigned long`**|Nullerweiterung|
|**`unsigned char`**|**`unsigned long long`**|Nullerweiterung|
|**`unsigned char`**|**`float`**|In **`long`** konvertieren, **`long`** in **`float`** konvertieren|
|**`unsigned char`**|**`double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|
|**`unsigned char`**|**`long double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|
|**`unsigned short`**|**`char`**|Niederwertiges Byte beibehalten|
|**`unsigned short`**|**`short`**|Bitmuster wird beibehalten; oberes Bit wird Vorzeichenbit|
|**`unsigned short`**|**`long`**|Nullerweiterung|
|**`unsigned short`**|**`long long`**|Nullerweiterung|
|**`unsigned short`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`unsigned short`**|**`unsigned long`**|Nullerweiterung|
|**`unsigned short`**|**`unsigned long long`**|Nullerweiterung|
|**`unsigned short`**|**`float`**|In **`long`** konvertieren, **`long`** in **`float`** konvertieren|
|**`unsigned short`**|**`double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|
|**`unsigned short`**|**`long double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|
|**`unsigned long`**|**`char`**|Niederwertiges Byte beibehalten|
|**`unsigned long`**|**`short`**|Niederwertiges Wort beibehalten|
|**`unsigned long`**|**`long`**|Bitmuster wird beibehalten; oberes Bit wird Vorzeichenbit|
|**`unsigned long`**|**`long long`**|Nullerweiterung|
|**`unsigned long`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`unsigned long`**|**`unsigned short`**|Niederwertiges Wort beibehalten|
|**`unsigned long`**|**`unsigned long long`**|Nullerweiterung|
|**`unsigned long`**|**`float`**|In **`long`** konvertieren, **`long`** in **`float`** konvertieren|
|**`unsigned long`**|**`double`**|Direktes Konvertieren in **`double`**|
|**`unsigned long`**|**`long double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|
|**`unsigned long long`**|**`char`**|Niederwertiges Byte beibehalten|
|**`unsigned long long`**|**`short`**|Niederwertiges Wort beibehalten|
|**`unsigned long long`**|**`long`**|Niederwertigen dword-Wert beibehalten|
|**`unsigned long long`**|**`long long`**|Bitmuster wird beibehalten; oberes Bit wird Vorzeichenbit|
|**`unsigned long long`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`unsigned long long`**|**`unsigned short`**|Niederwertiges Wort beibehalten|
|**`unsigned long long`**|**`unsigned long`**|Niederwertigen dword-Wert beibehalten|
|**`unsigned long long`**|**`float`**|In **`long`** konvertieren, **`long`** in **`float`** konvertieren|
|**`unsigned long long`**|**`double`**|Direktes Konvertieren in **`double`**|
|**`unsigned long long`**|**`long double`**|In **`long`** konvertieren, **`long`** in **`double`** konvertieren|

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
