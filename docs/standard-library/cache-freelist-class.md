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
ms.openlocfilehash: bbe0ff0f2297afcec99bd162ebe6a6d3e10f9bce
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560725"
---
# <a name="cache_freelist-class"></a>cache_freelist-Klasse

Definiert eine [Blockzuweisung](../standard-library/allocators-header.md), die Speicherblöcke einheitlicher Größe zuweist und freigibt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parameter

*RT*\
Die Anzahl der zuzuweisenden Elemente im Array

*Max*\
Die max-Klasse, die die maximale Größe der Freiliste angibt. Dies kann [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) oder [max_variable_size](../standard-library/max-variable-size-class.md) sein.

## <a name="remarks"></a>Bemerkungen

Die cache_freelist-Klassen Vorlage verwaltet eine freie Liste mit Speicherblöcken der Größe *SZ*. Wenn die freie Liste voll ist, verwendet Sie den **Operator Delete** zum Freigeben von Speicherblöcken. Wenn die Freiliste leer ist, verwendet Sie den **New-Operator** , um neue Speicherblöcke zuzuordnen. Die maximale Größe der Freiliste wird von der Klasse max-Klasse bestimmt, die im *Max* -Parameter übergeben wird.

Jeder Speicherblock enthält *SZ* -Bytes an nutzbarem Speicher und die Daten, die der **Operator new** und der **Operator Delete** erfordern.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[cache_freelist](#cache_freelist)|Konstruiert ein Objekt vom Typ `cache_freelist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Jugend](#allocate)|Belegt einen Speicherblock.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a> cache_freelist:: zuordnen

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a> cache_freelist:: cache_freelist

Konstruiert ein Objekt vom Typ `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a> cache_freelist::d ezuordnen

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
