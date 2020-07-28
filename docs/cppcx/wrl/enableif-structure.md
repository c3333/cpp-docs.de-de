---
title: EnableIf-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: f43166920f3582ab681b67d2c89563dcf78ff0f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220495"
---
# <a name="enableif-structure"></a>EnableIf-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ.

*b*<br/>
Ein boolescher Ausdruck.

## <a name="remarks"></a>Bemerkungen

Definiert einen Datenmember des Typs, der durch den zweiten Vorlagen Parameter angegeben wird, wenn der erste Vorlagen Parameter als ausgewertet wird **`true`** .

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`type`|Wenn der Vorlagen Parameter *b* als ausgewertet **`true`** wird, definiert die partielle Spezialisierung den Datenmember `type` vom Typ `T` .|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`EnableIf`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft:: WRL::D etails-Namespace](microsoft-wrl-details-namespace.md)
