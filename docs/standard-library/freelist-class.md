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
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317205"
---
# <a name="freelist-class"></a>freelist-Klasse

Verwaltet eine Liste von Speicherblöcken

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Sz*|Die Anzahl der zuzuweisenden Elemente im Array|
|*Max*|Die max-Klasse, die die maximale Anzahl von Elementen darstellt, die in der freien Liste gespeichert werden. Die Klasse kann [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md) oder [max_variable_size](../standard-library/max-variable-size-class.md) sein.|

## <a name="remarks"></a>Bemerkungen

Diese Klassenvorlage verwaltet eine Liste von Speicherblöcken der Größe *Sz* mit der maximalen Länge der Liste, die durch die in *Max*übergebene max-Klasse bestimmt wird.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[freelist](#freelist)|Konstruiert ein Objekt vom Typ `freelist`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[Pop](#pop)|Entfernt den ersten Speicherblock aus der freien Liste|
|[push](#push)|Fügt der Liste einen Speicherblock hinzu|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>freelist::freelist

Konstruiert ein Objekt vom Typ `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Bemerkungen

## <a name="freelistpop"></a><a name="pop"></a>freie Liste::pop

Entfernt den ersten Speicherblock aus der freien Liste

```cpp
void *pop();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Speicherblock zurück, der aus der Liste entfernt wurde

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion gibt NULL zurück, wenn die Liste leer ist. Andernfalls entfernt sie den ersten Speicherblock aus der Liste.

## <a name="freelistpush"></a><a name="push"></a>freelist::push

Fügt der Liste einen Speicherblock hinzu

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ptr*|Ein Zeiger auf den Speicherblock, der der freien Liste hinzugefügt werden soll|

### <a name="return-value"></a>Rückgabewert

**true,** `full` wenn die Funktion der max-Klasse **false**zurückgibt; Andernfalls gibt `push` die Funktion **false**zurück.

### <a name="remarks"></a>Bemerkungen

Wenn `full` die Funktion der max-Klasse **false**zurückgibt, fügt diese Memberfunktion den Speicherblock, auf den *ptr* zeigt, an den Kopf der Liste an.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
