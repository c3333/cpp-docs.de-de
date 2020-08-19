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
ms.openlocfilehash: 1ee422423356a18f1c81796790593a20dc03fbab
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560712"
---
# <a name="cache_chunklist-class"></a>cache_chunklist-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parameter

*RT*\
Die Anzahl der zuzuweisenden Elemente im Array

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage verwendet den **New-Operator** , um Segmente von unformatierten Arbeitsspeicher zuzuordnen, und subzuordnende Blöcke, um bei Bedarf Speicher für einen Speicherblock zuzuweisen. Er speichert frei zugeordnete Speicherblöcke in einer separaten freien Liste für jeden Block und verwendet den **Operator Delete** zum Aufheben der Zuordnung eines Segments, wenn kein Arbeitsspeicher Block verwendet wird.

Jeder Speicherblock enthält *SZ* -Bytes des verwendbaren Speichers und einen Zeiger auf den Block, zu dem er gehört. Jeder Block enthält `Nelts` Speicherblöcke, drei Zeiger, einen int-Wert und die Daten, die **Operator new** und **Operator Delete** erfordern.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[cache_chunklist](#cache_chunklist)|Konstruiert ein Objekt vom Typ `cache_chunklist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Jugend](#allocate)|Belegt einen Speicherblock.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a> Cache_chunklist:: zuordnen

Belegt einen Speicherblock.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parameter

*Countdown*\
Die Anzahl der zuzuweisenden Elemente im Array

### <a name="return-value"></a>Rückgabewert

Zeiger auf das zugewiesene Objekt.

### <a name="remarks"></a>Bemerkungen

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a> Cache_chunklist:: cache_chunklist

Konstruiert ein Objekt vom Typ `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a> Cache_chunklist::d ezuordnen

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

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
