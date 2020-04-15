---
title: cache_freelist-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366739"
---
# <a name="cache_freelist-class"></a>cache_freelist-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Sz*|Die Anzahl der zuzuweisenden Elemente im Array|
|*Max*|Die max-Klasse, die die maximale Größe der Freiliste angibt. Dies kann [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) oder [max_variable_size](../standard-library/max-variable-size-class.md) sein.|

## <a name="remarks"></a>Bemerkungen

Die cache_freelist Klassenvorlage verwaltet eine kostenlose Liste von Speicherblöcken der Größe *Sz*. Wenn die freie Liste voll ist, verwendet sie **Operator delete,** um Speicherblöcke zuzuweisen. Wenn die freie Liste leer ist, verwendet sie **den Operator new,** um neue Speicherblöcke zuzuweisen. Die maximale Größe der freien Liste wird durch die Klasse max bestimmt, die im *Parameter Max* übergeben wird.

Jeder Speicherblock enthält *Sz-Bytes* an nutzbarem Speicher und die Daten, die **der Operator new** und das Löschen des **Operators** benötigen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[Cache_freelist](#cache_freelist)|Konstruiert ein Objekt vom Typ `cache_freelist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Zuordnen](#allocate)|Belegt einen Speicherblock.|
|[Freigeben](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist::zuweisen

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist::cache_freelist

Konstruiert ein Objekt vom Typ `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::deallocate

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

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
