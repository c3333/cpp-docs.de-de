---
title: max_variable_size-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: 79e37d8c464a009e4a5196aeacc8d4a718e355b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370968"
---
# <a name="max_variable_size-class"></a>max_variable_size-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das die maximale Länge eines [freelist](../standard-library/freelist-class.md)-Objekts auf eine maximale Länge einschränkt, die annähernd proportional zur Anzahl von zugewiesenen Speicherblöcken ist.

## <a name="syntax"></a>Syntax

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[max_variable_size](#max_variable_size)|Konstruiert ein Objekt vom Typ `max_variable_size`.|

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

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size::zugeteilt

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_nx*|Der Inkrementwert|

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion fügt *dem* `_Nallocs`gespeicherten Wert _Nx hinzu. Diese Memberfunktion wird nach jedem `cache_freelist::allocate` erfolgreichen Aufruf des Operators **new**aufgerufen. Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Vom Operator **new**zugewiesenen Block.

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size::deallocated

Verringert die Anzahl der zugeordneten Speicherblöcke.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_nx*|Der Inkrementwert|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion subtrahiert *_Nx* vom gespeicherten Wert `_Nallocs`. Diese Memberfunktion wird nach `cache_freelist::deallocate` jedem Aufruf von operator **delete**aufgerufen. Das Argument *_Nx* ist die Anzahl der Speicherblöcke im Chunk Deallocated by operator **delete**.

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size::voll

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der **true**Aufruf `deallocate` true zurückgibt, wird der Speicherblock in der freien Liste angezeigt. Wenn false zurückgegeben `deallocate` wird, ruft operator **delete,** um den Block zu zuweisen.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size::max_variable_size

Konstruiert ein Objekt vom Typ `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor initialisiert die gespeicherten Werte `_Nblocks` und `_Nallocs` auf null.

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size::veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion verringert den gespeicherten `_Nblocks`-Wert. Die `released`-Memberfunktion der aktuellen max-Klasse wird von `cache_freelist::allocate` aufgerufen, wann immer ein Speicherblock aus der Freiliste entfernt wird.

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size::gerettet

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion inkrementiert den gespeicherten `_Nblocks`-Wert. Diese Memberfunktion wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
