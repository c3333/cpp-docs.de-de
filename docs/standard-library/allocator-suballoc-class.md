---
title: allocator_suballoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 47b82a198a52a61bd5558bd59a38b1d328fa67b2
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562583"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc-Klasse

Beschreibt ein Objekt, das die Speicher Belegung und-Freigabe für Objekte des Typs *Type mithilfe eines Caches vom Typ* [Cache_suballoc](cache-suballoc-class.md)verwaltet.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Elementtyp, die durch die Zuweisung zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung: `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
