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
ms.openlocfilehash: 53d2603c82e94710ed687dce4caeec24aeb2f60a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561647"
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
|[aufgehoben](#deallocated)|Verringert die Anzahl der zugeordneten Speicherblöcke.|
|[full](#full)|Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.|
|[gebracht](#released)|Verringert die Anzahl der Speicherblöcke auf der Freiliste.|
|[saved](#saved)|Erhöht die Anzahl der Speicherblöcke auf der Freiliste.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a> Max_variable_size:: zugeordnet

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion fügt *_Nx* dem gespeicherten Wert hinzu `_Nallocs` . Diese Member-Funktion wird nach jedem erfolgreichen Aufruf durch `cache_freelist::allocate` den-Operator aufgerufen **`new`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke im Block, der vom Operator zugeordnet wird **`new`** .

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a> Max_variable_size::d ezugeordnet

Verringert die Anzahl der zugeordneten Speicherblöcke.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Die Member-Funktion subtrahiert *_Nx* vom gespeicherten Wert `_Nallocs` . Diese Member-Funktion wird nach jedem Aufruf durch `cache_freelist::deallocate` den-Operator aufgerufen **`delete`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Block, dessen Zuordnung vom Operator aufgehoben wird **`delete`** .

## <a name="max_variable_sizefull"></a><a name="full"></a> Max_variable_size:: Full

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

**`true`** Wenn `_Nallocs / 16 + 16 <= _Nblocks` .

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der Aufruf zurückgegeben **`true`** wird, wird `deallocate` der Speicherblock in die freie Liste eingefügt; Wenn false zurückgegeben wird, `deallocate` Ruft Operator **`delete`** auf, um die Zuteilung des Blocks aufzulösen.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a> Max_variable_size:: Max_variable_size

Konstruiert ein Objekt vom Typ `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Bemerkungen

Dieser Konstruktor initialisiert die gespeicherten Werte `_Nblocks` und `_Nallocs` auf null.

## <a name="max_variable_sizereleased"></a><a name="released"></a> Max_variable_size:: veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion verringert den gespeicherten `_Nblocks`-Wert. Die `released`-Memberfunktion der aktuellen max-Klasse wird von `cache_freelist::allocate` aufgerufen, wann immer ein Speicherblock aus der Freiliste entfernt wird.

## <a name="max_variable_sizesaved"></a><a name="saved"></a> Max_variable_size:: gespeichert

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion inkrementiert den gespeicherten `_Nblocks`-Wert. Diese Memberfunktion wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
