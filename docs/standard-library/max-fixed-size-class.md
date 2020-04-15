---
title: max_fixed_size-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371006"
---
# <a name="max_fixed_size-class"></a>max_fixed_size-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Max*|Die max-Klasse, die die maximale Anzahl von Elementen zum Speichern in der `freelist` bestimmt.|

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[max_fixed_size](#max_fixed_size)|Konstruiert ein Objekt vom Typ `max_fixed_size`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[allocated](#allocated)|Erhöht die Anzahl der zugeordneten Speicherblöcke.|
|[Freigegeben](#deallocated)|Verringert die Anzahl der zugeordneten Speicherblöcke.|
|[Voll](#full)|Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.|
|[Freigegeben](#released)|Verringert die Anzahl der Speicherblöcke auf der Freiliste.|
|[saved](#saved)|Erhöht die Anzahl der Speicherblöcke auf der Freiliste.|

## <a name="requirements"></a>Anforderungen

**Header:** \<allocators>

**Namespace:** stdext

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::zugeteilt

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_nx*|Der Inkrementwert|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Diese Memberfunktion wird nach jedem `cache_freelist::allocate` erfolgreichen Aufruf des Operators **new**aufgerufen. Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Vom Operator **new**zugewiesenen Block.

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::deallocated

Verringert die Anzahl der zugeordneten Speicherblöcke.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_nx*|Der Inkrementwert|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Diese Memberfunktion wird nach `cache_freelist::deallocate` jedem Aufruf von operator **delete**aufgerufen. Das Argument *_Nx* ist die Anzahl der Speicherblöcke im Chunk Deallocated by operator **delete**.

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::voll

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn `Max <= _Nblocks`; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der **true**Aufruf `deallocate` true zurückgibt, wird der Speicherblock in der freien Liste angezeigt. Wenn false zurückgegeben `deallocate` wird, ruft operator **delete,** um den Block zu zuweisen.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Konstruiert ein Objekt vom Typ `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor initialisiert den gespeicherten Wert `_Nblocks` auf null.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Verringert den gespeicherten Wert `_Nblocks`. Die `released` Memberfunktion der aktuellen [max-Klasse](../standard-library/allocators-header.md) wird aufgerufen, `cache_freelist::allocate` wenn sie einen Speicherblock aus der freien Liste entfernt.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::gerettet

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion inkrementiert den gespeicherten `_Nblocks`-Wert. Diese Memberfunktion wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
