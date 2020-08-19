---
title: max_none-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: 41ada338d9b8546202ecd49ff975f9642f190ba0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560542"
---
# <a name="max_none-class"></a>max_none-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parameter

*Max*\
Die max-Klasse, die die maximale Anzahl von Elementen zum Speichern in der `freelist` bestimmt.

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

## <a name="max_noneallocated"></a><a name="allocated"></a> Max_none:: zugeordnet

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Sie wird nach jedem erfolgreichen Aufruf durch `cache_freelist::allocate` den-Operator aufgerufen **`new`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke im Block, der vom Operator zugeordnet wird **`new`** .

## <a name="max_nonedeallocated"></a><a name="deallocated"></a> Max_none::d ezugeordnet

Verringert die Anzahl der zugeordneten Speicherblöcke.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

*_Nx*\
Der Inkrementwert

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Diese Member-Funktion wird nach jedem Aufruf durch `cache_freelist::deallocate` den-Operator aufgerufen **`delete`** . Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Block, dessen Zuordnung vom Operator aufgehoben wird **`delete`** .

## <a name="max_nonefull"></a><a name="full"></a> Max_none:: Full

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

Diese Member-Funktion gibt immer zurück **`true`** .

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der Aufruf zurückgegeben **`true`** wird, wird `deallocate` der Speicherblock in die freie Liste eingefügt; wenn er zurückgegeben **`false`** wird, `deallocate` Ruft den Operator auf, **`delete`** um die Zuteilung des Blocks aufzulösen.

## <a name="max_nonereleased"></a><a name="released"></a> Max_none:: veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Die `released`-Memberfunktion der aktuellen max-Klasse wird von `cache_freelist::allocate` aufgerufen, wann immer ein Speicherblock aus der Freiliste entfernt wird.

## <a name="max_nonesaved"></a><a name="saved"></a> Max_none:: gespeichert

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Sie wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
