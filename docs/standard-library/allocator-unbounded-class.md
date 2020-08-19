---
title: allocator_unbounded-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: d9d82dd29ab86654020e13b39a8c9588ee0732e8
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561543"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded-Klasse

Beschreibt ein Objekt, das die Speicher Belegung und-Freigabe für Objekte des Typs *Type mithilfe eines Caches vom Typ* [cache_freelist](cache-freelist-class.md) mit einer Länge verwaltet, die von [Max_unbounded](max-unbounded-class.md)verwaltet wird.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Elementtyp, die durch die Zuweisung zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
