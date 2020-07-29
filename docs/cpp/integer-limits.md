---
title: Ganzzahlige Grenzen
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: a113dd687e6f135af950f461e024b9fd9feaf1b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213384"
---
# <a name="integer-limits"></a>Ganzzahlige Grenzen

**Microsoft-spezifisch**

Die Grenzwerte für ganzzahlige Typen sind in der folgenden Tabelle aufgeführt. Präprozessormakros für diese Grenzwerte werden ebenfalls definiert, wenn Sie die Standard Header Datei einschließen \<climits> .

## <a name="limits-on-integer-constants"></a>Grenzwerte für ganzzahlige Konstanten

| Konstante | Bedeutung | Wert |
|--|--|--|
| `CHAR_BIT` | Anzahl von Bits in der kleinsten Variable, die kein Bitfeld ist. | 8 |
| `SCHAR_MIN` | Minimalwert für eine Variable vom Typ **`signed char`** . | -128 |
| `SCHAR_MAX` | Maximalwert für eine Variable vom Typ **`signed char`** . | 127 |
| `UCHAR_MAX` | Maximalwert für eine Variable vom Typ **`unsigned char`** . | 255 (0xff) |
| `CHAR_MIN` | Minimalwert für eine Variable vom Typ **`char`** . | -128; 0, wenn die **`/J`** Option verwendet wird |
| `CHAR_MAX` | Maximalwert für eine Variable vom Typ **`char`** . | 127; 255 if- **`/J`** Option |
| `MB_LEN_MAX` | Maximale Anzahl von Bytes in einer Konstante mit mehreren Zeichen. | 5 |
| `SHRT_MIN` | Minimalwert für eine Variable vom Typ **`short`** . | -32768 |
| `SHRT_MAX` | Maximalwert für eine Variable vom Typ **`short`** . | 32767 |
| `USHRT_MAX` | Maximalwert für eine Variable vom Typ **`unsigned short`** . | 65535 (0xffff) |
| `INT_MIN` | Minimalwert für eine Variable vom Typ **`int`** . | -2147483648 |
| `INT_MAX` | Maximalwert für eine Variable vom Typ **`int`** . | 2147483647 |
| `UINT_MAX` | Maximalwert für eine Variable vom Typ **`unsigned int`** . | 4294967295 (0xffffffff) |
| `LONG_MIN` | Minimalwert für eine Variable vom Typ **`long`** . | -2147483648 |
| `LONG_MAX` | Maximalwert für eine Variable vom Typ **`long`** . | 2147483647 |
| `ULONG_MAX` | Maximalwert für eine Variable vom Typ **`unsigned long`** . | 4294967295 (0xffffffff) |
| `LLONG_MIN` | Minimalwert für eine Variable vom Typ**`long long`** | -9223372036854775808 |
| `LLONG_MAX` | Maximalwert für eine Variable vom Typ**`long long`** | 9223372036854775807 |
| `ULLONG_MAX` | Maximalwert für eine Variable vom Typ**`unsigned long long`** | 18446744073709551615 (0xffffffffffffffff) |

Wenn ein Wert die größte Ganzzahldarstellung übersteigt, generiert der Microsoft-Compiler einen Fehler.

## <a name="see-also"></a>Weitere Informationen

[Gleit Komma Begrenzungen](../cpp/floating-limits.md)
