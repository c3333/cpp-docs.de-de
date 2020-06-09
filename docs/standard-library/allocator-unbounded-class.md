---
title: allocator_unbounded-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: ba4c8b774752b327f5a4ede84fa804888cfd31d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617390"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded-Klasse

Beschreibt ein Objekt, das die Speicher Belegung und-Freigabe für Objekte des Typs *Type mithilfe eines Caches vom Typ* [cache_freelist](cache-freelist-class.md) mit einer Länge verwaltet, die von [Max_unbounded](max-unbounded-class.md)verwaltet wird.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Type*|Der Elementtyp, die durch die Zuweisung zugeordnet wird.|

## <a name="remarks"></a>Hinweise

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Siehe auch

[\<allocators>](allocators-header.md)
