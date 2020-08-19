---
title: sync_none-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: dac4dc1182de32af485d37a00ff96370ea8d8943
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562115"
---
# <a name="sync_none-class"></a>sync_none-Klasse

Beschreibt einen [Synchronisierungsfilter](../standard-library/allocators-header.md), der keine Synchronisierung bietet.

## <a name="syntax"></a>Syntax

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parameter

`Cache`\
Der Cachetyp, der diesem Synchronisierungsfilter zugeordnet werden soll. Dabei kann es [`cache_chunklist`](../standard-library/cache-chunklist-class.md) sich um, [`cache_freelist`](../standard-library/cache-freelist-class.md) oder handeln [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Jugend](#allocate)|Belegt einen Speicherblock.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|
|[equals](#equals)|Vergleicht zwei Caches auf Gleichheit.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a> Sync_none:: zuordnen

Belegt einen Speicherblock.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der zuzuweisenden Elemente im Array

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt `cache.allocate(count)` zurück, wobei `cache` das Cache-Objekt ist.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a> Sync_none::d ezuordnen

Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parameter

*PTR*\
Ein Zeiger auf das erste Objekt, dessen Zuordnung zum Speicherplatz aufgehoben werden soll.

*Countdown*\
Die Anzahl von Objekten, deren Zuweisung zum Speicherplatz aufgehoben werden soll.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ruft `cache.deallocate(ptr, count)` auf, wobei `cache` das Cache-Objekt darstellt.

## <a name="sync_noneequals"></a><a name="equals"></a> Sync_none:: ist Gleichheits

Vergleicht zwei Caches auf Gleichheit.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parameter

*Speichern*\
Das Cache-Objekt des Synchronisierungsfilters.

*Außer*\
Das Cache-Objekt, das auf Gleichheit verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Die Member-Funktion gibt immer zurück **`true`** .

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
