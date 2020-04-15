---
title: max_unbounded-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: fbc4351297ab8a3cc90a2a77fa31c3b134f10eab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370992"
---
# <a name="max_unbounded-class"></a>max_unbounded-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das ein [freelist](../standard-library/freelist-class.md)-Objekt nicht auf eine maximale Länge begrenzt.

## <a name="syntax"></a>Syntax

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a>max_unbounded::zugeteilt

Erhöht die Anzahl der zugeordneten Speicherblöcke.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*_nx*|Der Inkrementwert|

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Es wird nach jedem `cache_freelist::allocate` erfolgreichen Aufruf des Operators **new**aufgerufen. Das Argument *_Nx* ist die Anzahl der Speicherblöcke in dem Vom Operator **new**zugewiesenen Block.

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a>max_unbounded::deallocated

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

## <a name="max_unboundedfull"></a><a name="full"></a>max_unbounded::voll

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

Die Memberfunktion gibt immer **false**zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der **true**Aufruf `deallocate` true zurückgibt, wird der Speicherblock in der freien Liste angezeigt. Wenn false zurückgegeben `deallocate` wird, ruft operator **delete,** um den Block zu zuweisen.

## <a name="max_unboundedreleased"></a><a name="released"></a>max_unbounded::veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Die `released`-Memberfunktion der aktuellen max-Klasse wird von `cache_freelist::allocate` aufgerufen, wann immer ein Speicherblock aus der Freiliste entfernt wird.

## <a name="max_unboundedsaved"></a><a name="saved"></a>max_unbounded::gerettet

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Sie wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
