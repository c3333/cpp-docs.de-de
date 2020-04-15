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
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373428"
---
# <a name="rts_alloc-class"></a>rts_alloc-Klasse

Die rts_alloc-Klassenvorlage beschreibt einen [Filter,](../standard-library/allocators-header.md) der ein Array von Cacheinstanzen enthält, und bestimmt, welche Instanz zur Laufzeit anstelle von Kompilierungszeiten für die Zuweisung und Deallation verwendet werden soll.

## <a name="syntax"></a>Syntax

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Cache*|Der Typ der Cache-Instanzen, die im Array enthalten sind. Dieser kann eine [cache_chunklist-Klasse](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) oder [cache_suballoc](../standard-library/cache-suballoc-class.md) sein.|

## <a name="remarks"></a>Bemerkungen

Diese Klassenvorlage enthält mehrere Blockzuweisungsinstanzen und bestimmt, welche Instanz zur Laufzeit anstelle von Kompilierungszeiten für die Zuweisung oder Deallokation verwendet werden soll. Sie wird mit Compilern verwendet, die keine Neubindungen kompilieren können.

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Zuordnen](#allocate)|Belegt einen Speicherblock.|
|[Freigeben](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|
|[equals](#equals)|Vergleicht zwei Caches auf Gleichheit.|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::zuweisen

Belegt einen Speicherblock.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*count*|Die Anzahl der zuzuweisenden Elemente im Array|

### <a name="return-value"></a>Rückgabewert

Zeiger auf das zugewiesene Objekt.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `caches[_IDX].allocate(count)`gibt zurück, wobei der Index `_IDX` durch die *angeforderte*Blockgröße bestimmt `operator new(count)`wird, oder, wenn die *Anzahl* zu groß ist, gibt sie zurück. `cache`, das das Cache-Objekt darstellt.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::deallocate

Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ptr*|Ein Zeiger auf das erste Objekt, dessen Zuordnung zum Speicherplatz aufgehoben werden soll.|
|*count*|Die Anzahl von Objekten, deren Zuweisung zum Speicherplatz aufgehoben werden soll.|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `caches[_IDX].deallocate(ptr, count)`ruft auf `_IDX` , wobei der Index durch die *angeforderte*Blockgröße `operator delete(ptr)`bestimmt wird, oder, wenn die *Anzahl* zu groß ist, gibt sie zurück.

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc::gleich

Vergleicht zwei Caches auf Gleichheit.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_Cache*|Das Cache-Objekt, das dem Filter zugeordnet ist.|
|*_Other*|Das Cache-Objekt, das auf Gleichheit verglichen werden soll.|

### <a name="remarks"></a>Bemerkungen

**wahr,** wenn `caches[0].equals(other.caches[0])`das Ergebnis von ; andernfalls **false**. `caches` stellt das Array von Cache-Objekten dar.

## <a name="see-also"></a>Siehe auch

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<Zuallokatoren>](../standard-library/allocators-header.md)
