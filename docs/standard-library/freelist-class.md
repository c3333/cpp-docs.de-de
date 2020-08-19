---
title: freelist-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: bf88e33f5d00b9b6b90d2712a0bbabaa3e571340
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561205"
---
# <a name="freelist-class"></a>freelist-Klasse

Verwaltet eine Liste von Speicherblöcken

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parameter

*RT*\
Die Anzahl der zuzuweisenden Elemente im Array

*Max*\
Die max-Klasse, die die maximale Anzahl von Elementen darstellt, die in der freien Liste gespeichert werden. Die Klasse kann [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) oder [max_variable_size](../standard-library/max-variable-size-class.md) sein.

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage verwaltet eine Liste von Speicherblöcken der Größe- *SZ* mit der maximalen Länge der Liste, die durch die max-Klasse festgelegt wird, *die maximal überschritten wird.*

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[freelist](#freelist)|Konstruiert ein Objekt vom Typ `freelist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Chor](#pop)|Entfernt den ersten Speicherblock aus der freien Liste|
|[push](#push)|Fügt der Liste einen Speicherblock hinzu|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a> FreeList:: FreeList

Konstruiert ein Objekt vom Typ `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="freelistpop"></a><a name="pop"></a> FreeList::p op

Entfernt den ersten Speicherblock aus der freien Liste

```cpp
void *pop();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Speicherblock zurück, der aus der Liste entfernt wurde

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion gibt NULL zurück, wenn die Liste leer ist. Andernfalls entfernt sie den ersten Speicherblock aus der Liste.

## <a name="freelistpush"></a><a name="push"></a> FreeList::p USH

Fügt der Liste einen Speicherblock hinzu

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parameter

*PTR*\
Ein Zeiger auf den Speicherblock, der der freien Liste hinzugefügt werden soll

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die- `full` Funktion der Max-Klasse zurückgibt **`false`** , andernfalls `push` gibt die Funktion zurück **`false`** .

### <a name="remarks"></a>Bemerkungen

Wenn die- `full` Funktion der Max-Klasse zurückgibt **`false`** , fügt diese Member-Funktion den Speicherblock hinzu, auf den *ptr* zeigt, auf den Anfang der Liste.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
