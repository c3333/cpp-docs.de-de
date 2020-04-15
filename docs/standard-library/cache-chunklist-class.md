---
title: cache_chunklist-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366755"
---
# <a name="cache_chunklist-class"></a>cache_chunklist-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Sz*|Die Anzahl der zuzuweisenden Elemente im Array|

## <a name="remarks"></a>Bemerkungen

Diese Klassenvorlage verwendet **Operator new,** um Blöcke von Rohspeicher zuzuweisen und Blöcke zu unterordnen, um Speicher für einen Speicherblock bei Bedarf zuzuweisen. Es speichert verteilte Speicherblöcke in einer separaten freien Liste für jeden Chunk und verwendet **Operator delete,** um einen Chunk zuzuweisen, wenn keiner seiner Speicherblöcke verwendet wird.

Jeder Speicherblock enthält *Sz-Bytes* an nutzbarem Speicher und einen Zeiger auf den Chunk, zu dem er gehört. Jeder Chunk `Nelts` enthält Speicherblöcke, drei Zeiger, einen int und die Daten, die **der Operator neu** und das Löschen des **Operators** benötigen.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[cache_chunklist](#cache_chunklist)|Konstruiert ein Objekt vom Typ `cache_chunklist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Zuordnen](#allocate)|Belegt einen Speicherblock.|
|[Freigeben](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist::zuweisen

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Konstruiert ein Objekt vom Typ `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::deallocate

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
