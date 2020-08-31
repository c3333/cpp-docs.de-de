---
title: dendian-Aufzählung
description: Enumeration, die verwendet wird, um die Enumeration von skalaren Typen anzugeben.
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: 78df181e20d0e5d72508bd0fc86118528a312d6b
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194759"
---
# <a name="endian-enum"></a>dendian-Aufzählung

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

## <a name="requirements"></a>Anforderungen

**Header:**\<bit>

**Namespace:** std

`/std:c++latest` ist erforderlich

## <a name="see-also"></a>Weitere Informationen

[\<bit>](../standard-library/bit.md)  
