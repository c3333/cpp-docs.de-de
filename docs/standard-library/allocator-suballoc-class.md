---
title: allocator_suballoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 01d282585133d55ee3f7ec96c212705c2afca9d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617421"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc-Klasse

Beschreibt ein Objekt, das die Speicher Belegung und-Freigabe für Objekte des Typs *Type mithilfe eines Caches vom Typ* [Cache_suballoc](cache-suballoc-class.md)verwaltet.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Type*|Der Elementtyp, die durch die Zuweisung zugeordnet wird.|

## <a name="remarks"></a>Hinweise

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Siehe auch

[\<allocators>](allocators-header.md)
