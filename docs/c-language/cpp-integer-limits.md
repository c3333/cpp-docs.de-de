---
title: Integer-Grenzwerte in C und C++
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 1484b43719696578be437909351e24a550ec9869
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217115"
---
# <a name="c-and-c-integer-limits"></a>Integer-Grenzwerte in C und C++

**Microsoft-spezifisch**

Die Grenzwerte für Integer-Datentypen in C und C++ sind in der folgenden Tabelle aufgeführt. Diese Grenzwerte werden in der Standardheaderdatei `<limits.h>` definiert. Der C++-Standardbibliotheksheader `<limits>` enthält `<climits>`, worin `<limits.h>` enthalten ist.

Microsoft C ermöglicht zudem die Deklaration von Variablen für ganze Zahlen mit angegebener Größe, die integrale Typen der Größe 8-, 16-, 32- oder 64-Bit sind. Weitere Informationen über ganze Zahlen mit angepasster Größe in C finden Sie unter [Integer-Datentypen mit angegebener Größe](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Grenzwerte für ganzzahlige Konstanten

|**Konstante**|Bedeutung|Wert|
|------------------|-------------|-----------|
|**CHAR_BIT**|Anzahl von Bits in der kleinsten Variable, die kein Bitfeld ist.|8|
|**SCHAR_MIN**|Mindestwert für eine Variable vom Typ **`signed char`** .|-128|
|**SCHAR_MAX**|Maximalwert für eine Variable vom Typ **`signed char`** .|127|
|**UCHAR_MAX**|Maximalwert für eine Variable vom Typ **`unsigned char`** .|255 (0xff)|
|**CHAR_MIN**|Mindestwert für eine Variable vom Typ **`char`** .|-128; 0 wenn /J-Option verwendet|
|**CHAR_MAX**|Maximalwert für eine Variable vom Typ **`char`** .|127; 255 wenn /J-Option verwendet|
|**MB_LEN_MAX**|Maximale Anzahl von Bytes in einer Konstante mit mehreren Zeichen.|5|
|**SHRT_MIN**|Mindestwert für eine Variable vom Typ **`short`** .|-32768|
|**SHRT_MAX**|Maximalwert für eine Variable vom Typ **`short`** .|32767|
|**USHRT_MAX**|Maximalwert für eine Variable vom Typ **`unsigned short`** .|65535 (0xffff)|
|**INT_MIN**|Mindestwert für eine Variable vom Typ **`int`** .|-2147483647 - 1|
|**INT_MAX**|Maximalwert für eine Variable vom Typ **`int`** .|2147483647|
|**UINT_MAX**|Maximalwert für eine Variable vom Typ **`unsigned int`** .|4294967295 (0xffffffff)|
|**LONG_MIN**|Mindestwert für eine Variable vom Typ **`long`** .|-2147483647 - 1|
|**LONG_MAX**|Maximalwert für eine Variable vom Typ **`long`** .|2147483647|
|**ULONG_MAX**|Maximalwert für eine Variable vom Typ **`unsigned long`** .|4294967295 (0xffffffff)|
|**LLONG_MIN**|Mindestwert für eine Variable vom Typ **`long long`** .|-9,223,372,036,854,775,807 - 1|
|**LLONG_MAX**|Maximalwert für eine Variable vom Typ **`long long`** .|9,223,372,036,854,775,807|
|**ULLONG_MAX**|Maximalwert für eine Variable vom Typ **`unsigned long long`** .|18,446,744,073,709,551,615 (0xffffffffffffffff)|

Wenn ein Wert die größte Ganzzahldarstellung übersteigt, generiert der Microsoft-Compiler einen Fehler.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Ganzzahlkonstanten](../c-language/c-integer-constants.md)
