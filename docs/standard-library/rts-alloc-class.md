---
title: rts_alloc-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: f422b171c14695a1207a30419a10d50cdfb5adf0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228127"
---
# <a name="rts_alloc-class"></a>rts_alloc-Klasse

Die Rts_alloc-Klassen Vorlage beschreibt einen [Filter](../standard-library/allocators-header.md) , der ein Array von Cache Instanzen enthält und bestimmt, welche Instanz für die Zuordnung und Aufhebung der Zuordnung zur Laufzeit anstatt zur Kompilierzeit verwendet werden soll.

## <a name="syntax"></a>Syntax

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Cache*|Der Typ der Cache-Instanzen, die im Array enthalten sind. Dieser kann eine [cache_chunklist-Klasse](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) oder [cache_suballoc](../standard-library/cache-suballoc-class.md) sein.|

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage enthält mehrere Block Belegungs Instanzen und bestimmt, welche Instanz zur Laufzeit anstelle der Kompilierzeit für die Zuordnung oder Aufhebung der Zuordnung verwendet werden soll. Sie wird mit Compilern verwendet, die keine Neubindungen kompilieren können.

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[allocate](#allocate)|Belegt einen Speicherblock.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|
|[equals](#equals)|Vergleicht zwei Caches auf Gleichheit.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>Rts_alloc:: zuordnen

Belegt einen Speicherblock.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*count*|Die Anzahl der zuzuweisenden Elemente im Array|

### <a name="return-value"></a>Rückgabewert

Zeiger auf das zugewiesene Objekt.

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt zurück `caches[_IDX].allocate(count)` , wobei der Index `_IDX` durch die angeforderte Block *count*Größe bestimmt wird, oder wenn *count* zu groß ist, wird zurückgegeben `operator new(count)` . `cache`, das das Cache-Objekt darstellt.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>Rts_alloc::d ezuordnen

Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ptr*|Ein Zeiger auf das erste Objekt, dessen Zuordnung zum Speicherplatz aufgehoben werden soll.|
|*count*|Die Anzahl von Objekten, deren Zuweisung zum Speicherplatz aufgehoben werden soll.|

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion ruft `caches[_IDX].deallocate(ptr, count)` auf, wobei der Index `_IDX` durch die angeforderte Block *count*Größe bestimmt wird, oder wenn *count* zu groß ist, wird zurückgegeben `operator delete(ptr)` .

## <a name="rts_allocequals"></a><a name="equals"></a>Rts_alloc:: ist Gleichheits

Vergleicht zwei Caches auf Gleichheit.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*_Cache*|Das Cache-Objekt, das dem Filter zugeordnet ist.|
|*_Other*|Das Cache-Objekt, das auf Gleichheit verglichen werden soll.|

### <a name="remarks"></a>Bemerkungen

**`true`**, wenn das Ergebnis von `caches[0].equals(other.caches[0])` ist, andernfalls **`false`** . `caches` stellt das Array von Cache-Objekten dar.

## <a name="see-also"></a>Siehe auch

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
