---
title: allocator_variable_size-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: 24769962d615c75f4573a6261b6000fadf39b218
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561348"
---
# <a name="allocator_variable_size-class"></a>allocator_variable_size-Klasse

Beschreibt ein Objekt, das die Speicher Belegung und-Freigabe für Objekte des Typs *Type mithilfe eines Caches vom Typ* [cache_freelist](cache-freelist-class.md) mit einer Länge verwaltet, die von [Max_variable_size](max-variable-size-class.md)verwaltet wird.

## <a name="syntax"></a>Syntax

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Parameter

*Sorte*\
Der Elementtyp, die durch die Zuweisung zugeordnet wird.

## <a name="remarks"></a>Bemerkungen

Das [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) -Makro übergibt diese Klasse als *Name* -Parameter in der folgenden Anweisung: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
