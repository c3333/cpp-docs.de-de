---
title: EnableIf-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 44c6293b56e9e03c23d0d8cebf2a112e6fcf3664
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214031"
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

Definiert einen Datenmember des Typs, der durch den zweiten Vorlagen Parameter angegeben wird, wenn der erste Vorlagen Parameter als **true**ausgewertet wird.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`type`|Wenn der Vorlagen Parameter *b* als **true**ausgewertet wird, definiert die partielle Spezialisierung das Datenmember-`type` vom Typ `T`.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`EnableIf`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
