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
ms.openlocfilehash: c2342d068293714871b3f79675dd0d0b9db83448
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617545"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist-Klasse

Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte, die einen Zwischenspeicher des Typs [cache_chunklist](cache-chunklist-class.md) verwenden.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Type*|Der Elementtyp, die durch die Zuweisung zugeordnet wird.|

## <a name="remarks"></a>Hinweise

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung:`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Siehe auch

[\<allocators>](allocators-header.md)
