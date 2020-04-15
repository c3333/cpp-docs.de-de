---
title: cache_suballoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366731"
---
# <a name="cache_suballoc-class"></a>cache_suballoc-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Sz*|Die Anzahl der zuzuweisenden Elemente im Array|

## <a name="remarks"></a>Bemerkungen

Die cache_suballoc-Klassenvorlage speichert verteilte Speicherblöcke in einer freien `freelist<sizeof(Type), max_unbounded>`Liste mit unbegrenzter Länge, verwendet , und unterordnet Speicherblöcke aus einem größeren Block, der dem **Operator new** zugeordnet ist, wenn die freie Liste leer ist.

Jeder Chunk `Sz * Nelts` enthält Bytes an nutzbarem Speicher, und die Daten, die der **Operator new** und **das Löschen** des Operators benötigen. Zugeordnete Blöcke werden niemals freigegeben.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[cache_suballoc](#cache_suballoc)|Konstruiert ein Objekt vom Typ `cache_suballoc`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Zuordnen](#allocate)|Belegt einen Speicherblock.|
|[Freigeben](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc::zuweisen

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc::cache_suballoc

Konstruiert ein Objekt vom Typ `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc::deallocate

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
