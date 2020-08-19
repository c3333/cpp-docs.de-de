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
ms.openlocfilehash: 410cdc7bd45c54c252ce33c7d8e3e2f883ac0eb4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560620"
---
# <a name="cache_suballoc-class"></a>cache_suballoc-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parameter

*RT*\
Die Anzahl der zuzuweisenden Elemente im Array

## <a name="remarks"></a>Bemerkungen

In der Cache_suballoc-Klassen Vorlage werden die frei zugeordneten Speicherblöcke in einer freien Liste mit unbegrenzter Länge gespeichert. dabei wird verwendet `freelist<sizeof(Type), max_unbounded>` , und die Speicherblöcke werden von einem größeren Block, der mit **Operator new** zugeordnet wird, zugeordnet, wenn die freie Liste leer ist.

Jeder Block enthält `Sz * Nelts` Bytes des verwendbaren Speichers und die Daten, die der **Operator new** und der **Operator Delete** erfordern. Zugeordnete Blöcke werden niemals freigegeben.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[cache_suballoc](#cache_suballoc)|Konstruiert ein Objekt vom Typ `cache_suballoc`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Jugend](#allocate)|Belegt einen Speicherblock.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a> Cache_suballoc:: zuordnen

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a> Cache_suballoc:: Cache_suballoc

Konstruiert ein Objekt vom Typ `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a> Cache_suballoc::d ezuordnen

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
