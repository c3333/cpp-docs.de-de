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
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998726"
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

In der folgenden Tabelle sind die Konvertierungen von ganzzahligen Typen mit Vorzeichen zusammengefasst. Es wird davon ausgegangen, dass der Typ **char** standardmäßig ein Vorzeichen aufweist. Wenn Sie eine Kompilierzeitoption verwenden, um den Standardwert für den **char**-Typ in einen Typ ohne Vorzeichen zu ändern, gelten anstelle der Konvertierungen in dieser Tabelle die Konvertierungen aus der Tabelle [Conversions from Unsigned Integral Types](../c-language/conversions-from-unsigned-integral-types.md) (Konvertierungen von integralen Typen ohne Vorzeichen) für den Typ **unsigned char**.

**Microsoft-spezifisch**

Im Microsoft-Compiler sind **int** und **long** eindeutige aber äquivalente Typen. Die Konvertierung eines **int**-Werts wird auf dieselbe Weise wie die Konvertierung eines **long**-Werts ausgeführt.

**Ende Microsoft-spezifisch**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabelle mit Konvertierungen von integralen Typen mit Vorzeichen

|Von|Beschreibung|Methode|
|----------|--------|------------|
|**char**<sup>1</sup>|**short**|Signaturerweiterung|
|**char**|**long**|Signaturerweiterung|
|**char**|**langes long**|Signaturerweiterung|
|**char**|**unsigned char**|Muster beibehalten; oberes Bit verliert Funktion als Vorzeichenbit|
|**char**|**unsigned short**|Signaturerweiterung auf **short**; Konvertieren von **short** in **unsigned short**|
|**char**|**unsigned long**|Signaturerweiterung auf **long**; Konvertieren von **long** in **unsigned long**|
|**char**|**unsigned long long**|Signaturerweiterung auf **long long**; Konvertieren von **long long** in **unsigned long long**|
|**char**|**float**|Signaturerweiterung auf **long**; Konvertieren von **long** in **float**|
|**char**|**double**|Signaturerweiterung auf **long**; Konvertieren von **long** in **double**|
|**char**|**long double**|Signaturerweiterung auf **long**; Konvertieren von **long** in **double**|
|**short**|**char**|Niederwertiges Byte beibehalten|
|**short**|**long**|Signaturerweiterung|
|**short**|**langes long**|Signaturerweiterung|
|**short**|**unsigned char**|Niederwertiges Byte beibehalten|
|**short**|**unsigned short**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**short**|**unsigned long**|Signaturerweiterung auf **long**; Konvertieren von **long** in **unsigned long**|
|**short**|**unsigned long long**|Signaturerweiterung auf **long long**; Konvertieren von **long long** in **unsigned long long**|
|**short**|**float**|Signaturerweiterung auf **long**; Konvertieren von **long** in **float**|
|**short**|**double**|Signaturerweiterung auf **long**; Konvertieren von **long** in **double**|
|**short**|**long double**|Signaturerweiterung auf **long**; Konvertieren von **long** in **double**|
|**long**|**char**|Niederwertiges Byte beibehalten|
|**long**|**short**|Niederwertiges Wort beibehalten|
|**long**|**langes long**|Signaturerweiterung|
|**long**|**unsigned char**|Niederwertiges Byte beibehalten|
|**long**|**unsigned short**|Niederwertiges Wort beibehalten|
|**long**|**unsigned long**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**long**|**unsigned long long**|Signaturerweiterung auf **long long**; Konvertieren von **long long** in **unsigned long long**|
|**long**|**float**|Darstellen als **float**. Wenn **long** nicht genau dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**long**|**double**|Darstellen als **double**. Wenn **long** nicht genau als **double** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**long**|**long double**|Darstellen als **double**. Wenn **long** nicht genau als **double** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**langes long**|**char**|Niederwertiges Byte beibehalten|
|**langes long**|**short**|Niederwertiges Wort beibehalten|
|**langes long**|**long**|Niederwertigen dword-Wert beibehalten|
|**langes long**|**unsigned char**|Niederwertiges Byte beibehalten|
|**langes long**|**unsigned short**|Niederwertiges Wort beibehalten|
|**langes long**|**unsigned long**|Niederwertigen dword-Wert beibehalten|
|**langes long**|**unsigned long long**|Bitmuster beibehalten; höherwertiges Bit verliert Funktion als Vorzeichenbit|
|**langes long**|**float**|Darstellen als **float**. Wenn **long long** nicht genau dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**langes long**|**double**|Darstellen als **double**. Wenn **long long** nicht genau als **double** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|
|**langes long**|**long double**|Darstellen als **double**. Wenn **long long** nicht genau als **double** dargestellt werden kann, wirkt sich dies auf die Genauigkeit aus.|

<sup>1</sup> Bei allen **cha**r-Einträgen wird davon ausgegangen, dass der **char**-Typ standardmäßig ein Vorzeichen aufweist.

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
