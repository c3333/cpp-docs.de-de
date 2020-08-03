---
title: Konvertierungen von ganzzahligen Typen mit Vorzeichen
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: d41d2fd205a87f9f2be2179ffd8e38256a96e4f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226476"
---
# <a name="conversions-from-signed-integral-types"></a>Konvertierungen von ganzzahligen Typen mit Vorzeichen

Wenn eine ganze Zahl mit Vorzeichen in einen Integer- oder einen Gleitkommatyp konvertiert wird, bleibt der Wert unverändert, falls der ursprüngliche Wert im Ergebnistyp darstellbar ist.

Wenn eine ganze Zahl mit Vorzeichen in eine größere ganze Zahl konvertiert wird, wird der Wert mit einem Vorzeichen erweitert. Wenn sie in eine kleinere ganze Zahl konvertiert wird, werden die höherwertigen Bits abgeschnitten. Das Ergebnis wird mithilfe des Ergebnistyps wie in diesem Beispiel gezeigt interpretiert:

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Beim Konvertieren einer ganzen Zahl mit Vorzeichen in einen Gleitkommatyp ist das Ergebnis, falls der ursprüngliche Wert nicht genau im Ergebnistyp darstellbar ist, der nächsthöhere oder -niedrigere darstellbare Wert.

Informationen über die Größen der Integer- und Gleitkommatypen finden Sie unter [Speicherverwendung der grundlegenden Typen](../c-language/storage-of-basic-types.md).

In der folgenden Tabelle sind die Konvertierungen von ganzzahligen Typen mit Vorzeichen zusammengefasst. Es wird davon ausgegangen, dass der Typ **`char`** standardmäßig ein Vorzeichen aufweist. Wenn Sie eine Kompilierzeitoption verwenden, um den Standardwert für den **`char`** -Typ in einen Typ ohne Vorzeichen zu ändern, gelten anstelle der Konvertierungen in dieser Tabelle die Konvertierungen aus der Tabelle [Konvertierungen von integralen Typen ohne Vorzeichen](../c-language/conversions-from-unsigned-integral-types.md) für den Typ **`unsigned char`** .

**Microsoft-spezifisch**

Im Microsoft-Compiler sind **`int`** und **`long`** eindeutige aber äquivalente Typen. Die Konvertierung eines **`int`** -Werts wird auf dieselbe Weise wie die Konvertierung eines **`long`** -Werts ausgeführt.

**Ende Microsoft-spezifisch**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabelle mit Konvertierungen von integralen Typen mit Vorzeichen

|Von|Beschreibung|Methode|
|----------|--------|------------|
|**`char`** <sup>1</sup>|**`short`**|Signaturerweiterung|
|**`char`**|**`long`**|Signaturerweiterung|
|**`char`**|**`long long`**|Signaturerweiterung|
|**`char`**|**`unsigned char`**|Muster beibehalten; oberes Bit verliert Funktion als Vorzeichenbit|
|**`char`**|**`unsigned short`**|Vorzeichenerweiterung zu **`short`** ; Konvertieren von **`short`** zu **`unsigned short`**|
|**`char`**|**`unsigned long`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`unsigned long`**|
|**`char`**|**`unsigned long long`**|Vorzeichenerweiterung zu **`long long`** ; Konvertieren von **`long long`** zu **`unsigned long long`**|
|**`char`**|**`float`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`float`**|
|**`char`**|**`double`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`double`**|
|**`char`**|**`long double`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`double`**|
|**`short`**|**`char`**|Niederwertiges Byte beibehalten|
|**`short`**|**`long`**|Signaturerweiterung|
|**`short`**|**`long long`**|Signaturerweiterung|
|**`short`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`short`**|**`unsigned short`**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**`short`**|**`unsigned long`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`unsigned long`**|
|**`short`**|**`unsigned long long`**|Vorzeichenerweiterung zu **`long long`** ; Konvertieren von **`long long`** zu **`unsigned long long`**|
|**`short`**|**`float`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`float`**|
|**`short`**|**`double`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`double`**|
|**`short`**|**`long double`**|Vorzeichenerweiterung zu **`long`** ; Konvertieren von **`long`** zu **`double`**|
|**`long`**|**`char`**|Niederwertiges Byte beibehalten|
|**`long`**|**`short`**|Niederwertiges Wort beibehalten|
|**`long`**|**`long long`**|Signaturerweiterung|
|**`long`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`long`**|**`unsigned short`**|Niederwertiges Wort beibehalten|
|**`long`**|**`unsigned long`**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**`long`**|**`unsigned long long`**|Vorzeichenerweiterung zu **`long long`** ; Konvertieren von **`long long`** zu **`unsigned long long`**|
|**`long`**|**`float`**|Darstellen als **`float`** . Wenn **`long`** nicht genau dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**`long`**|**`double`**|Darstellen als **`double`** . Wenn **`long`** nicht genau als **`double`** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**`long`**|**`long double`**|Darstellen als **`double`** . Wenn **`long`** nicht genau als **`double`** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**`long long`**|**`char`**|Niederwertiges Byte beibehalten|
|**`long long`**|**`short`**|Niederwertiges Wort beibehalten|
|**`long long`**|**`long`**|Niederwertigen dword-Wert beibehalten|
|**`long long`**|**`unsigned char`**|Niederwertiges Byte beibehalten|
|**`long long`**|**`unsigned short`**|Niederwertiges Wort beibehalten|
|**`long long`**|**`unsigned long`**|Niederwertigen dword-Wert beibehalten|
|**`long long`**|**`unsigned long long`**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**`long long`**|**`float`**|Darstellen als **`float`** . Wenn **`long long`** nicht genau dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**`long long`**|**`double`**|Darstellen als **`double`** . Wenn **`long long`** nicht genau als **`double`** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**`long long`**|**`long double`**|Darstellen als **`double`** . Wenn **`long long`** nicht genau als **`double`** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|

<sup>1</sup> Bei allen **`char`** -Einträgen wird davon ausgegangen, dass der **`char`** -Typ standardmäßig ein Vorzeichen hat.

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
