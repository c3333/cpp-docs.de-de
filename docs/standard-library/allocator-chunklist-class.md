---
title: allocator_chunklist-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 64b419b2565609d8f6018facdbe25d5dee9d94aa
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562622"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist-Klasse

Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte, die einen Zwischenspeicher des Typs [cache_chunklist](cache-chunklist-class.md) verwenden.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Elementtyp, die durch die Zuweisung zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
