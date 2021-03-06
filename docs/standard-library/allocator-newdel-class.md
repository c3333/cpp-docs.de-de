---
title: allocator_newdel-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: 30e0f7902a8af435b46aaedf0b38661b7a6604a8
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562596"
---
# <a name="allocator_newdel-class"></a>allocator_newdel-Klasse

Implementiert einen Allocator, der den **Operator Delete** verwendet, um einen Speicherblock freizugeben, und den **New-Operator** , um einen Speicherblock zuzuweisen.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Elementtyp, die durch die Zuweisung zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung: `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
