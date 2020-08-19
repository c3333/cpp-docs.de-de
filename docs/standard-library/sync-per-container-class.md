---
title: sync_per_container-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 51a88e6ec4eca693c652635e1574e3611d7217cd
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562102"
---
# <a name="sync_per_container-class"></a>sync_per_container-Klasse

Beschreibt einen [Synchronisierungsfilter](../standard-library/allocators-header.md), der für jedes Zuweisungsobjekt ein getrenntes Cache-Objekt bereitstellt.

## <a name="syntax"></a>Syntax

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Parameter

*Speichern*\
Der Cachetyp, der diesem Synchronisierungsfilter zugeordnet werden soll. Dabei kann es [`cache_chunklist`](../standard-library/cache-chunklist-class.md) sich um, [`cache_freelist`](../standard-library/cache-freelist-class.md) oder handeln [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[equals](#equals)|Vergleicht zwei Caches auf Gleichheit.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a> Sync_per_container:: ist Gleichheits

Vergleicht zwei Caches auf Gleichheit.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parameter

*Speichern*\
Das Cache-Objekt des Synchronisierungsfilters.

*Außer*\
Das Cache-Objekt, das auf Gleichheit verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Die Member-Funktion gibt immer zurück **`false`** .

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
