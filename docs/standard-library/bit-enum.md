---
title: endian-Enumerator
description: Enumeration, die verwendet wird, um die Enumeration von skalaren Typen anzugeben.
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: b535bc009fbdc0b047444a6bc2ca36eed7a6d1cb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040079"
---
# <a name="endian-enum"></a>endian-Enumerator

Gibt die enumerität aller skalaren Typen an.

## <a name="syntax"></a>Syntax

```cpp
enum class endian {
    little = 0,
    big = 1,
    native = little
 };
```

### <a name="members"></a>Member

|Element|BESCHREIBUNG|
|-|-|
| `little` | Gibt an, dass skalare Typen Little--Enumerationstyp sind. Das heißt, das am wenigsten signifikante Byte wird in der kleinsten Adresse gespeichert. Beispielsweise `0x1234` wird gespeichert `0x34` `0x12` .  |
| `big` | Gibt an, dass skalare Typen Big-Endian sind, d. h., das signifikanteste Byte wird in der kleinsten Adresse gespeichert. Beispielsweise `0x1234` wird gespeichert `0x12` `0x34` .  |

## <a name="remarks"></a>Bemerkungen

Alle nativen skalaren Typen sind Little-Endian für die Plattformen, die Microsoft Visual C++ Ziele (x86, x64, arm, ARM64).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<bit>

**Namespace:** std

[/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[\<bit>](../standard-library/bit.md)  
