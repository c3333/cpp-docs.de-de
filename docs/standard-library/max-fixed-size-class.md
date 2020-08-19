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
ms.openlocfilehash: e62884c83d71b4e9f1902fa4bc7f52f5e0a4e0ee
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561686"
---
# <a name="max_fixed_size-class"></a>max_fixed_size-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parameter

*Max*\
Die max-Klasse, die die maximale Anzahl von Elementen zum Speichern in der `freelist` bestimmt.

### <a name="constructors"></a>Konstruktoren

|Konstruktor|BESCHREIBUNG|
|-|-|
|[max_fixed_size](#max_fixed_size)|Konstruiert ein Objekt vom Typ `max_fixed_size`.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[allocated](#allocated)|Erhöht die Anzahl der zugeordneten Speicherblöcke.|
|[aufgehoben](#deallocated)|Verringert die Anzahl der zugeordneten Speicherblöcke.|
|[full](#full)|Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.|
|[gebracht](#released)|Verringert die Anzahl der Speicherblöcke auf der Freiliste.|
|[saved](#saved)|Erhöht die Anzahl der Speicherblöcke auf der Freiliste.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a> Max_fixed_size:: zugeordnet

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Diese Member-Funktion wird nach jedem erfolgreichen Aufruf durch `cache_freelist::allocate` den-Operator aufgerufen **`new`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke im Block, der vom Operator zugeordnet wird **`new`** .

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a> Max_fixed_size::d ezugeordnet

Verringert die Anzahl der zugeordneten Speicherblöcke.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Diese Member-Funktion wird nach jedem Aufruf durch `cache_freelist::deallocate` den-Operator aufgerufen **`delete`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Block, dessen Zuordnung vom Operator aufgehoben wird **`delete`** .

## <a name="max_fixed_sizefull"></a><a name="full"></a> Max_fixed_size:: Full

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

**`true`**`Max <= _Nblocks`, wenn, andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der Aufruf zurückgegeben **`true`** wird, wird `deallocate` der Speicherblock in die freie Liste eingefügt; Wenn false zurückgegeben wird, `deallocate` Ruft Operator **`delete`** auf, um die Zuteilung des Blocks aufzulösen.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a> Max_fixed_size:: Max_fixed_size

Konstruiert ein Objekt vom Typ `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor initialisiert den gespeicherten Wert `_Nblocks` auf null.

## <a name="max_fixed_sizereleased"></a><a name="released"></a> Max_fixed_size:: veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Verringert den gespeicherten Wert `_Nblocks`. Die `released` Member-Funktion der aktuellen [max-Klasse](../standard-library/allocators-header.md) wird von aufgerufen, `cache_freelist::allocate` Wenn ein Speicherblock aus der freien Liste entfernt wird.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a> Max_fixed_size:: gespeichert

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion inkrementiert den gespeicherten `_Nblocks`-Wert. Diese Memberfunktion wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
