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
ms.openlocfilehash: c49ceec72be62d8ff3125f04d97bbb6952501677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370979"
---
# <a name="max_none-class"></a>max_none-Klasse

Beschreibt ein Objekt der [max-Klasse](../standard-library/allocators-header.md), das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Max*|Die max-Klasse, die die maximale Anzahl von Elementen zum Speichern in der `freelist` bestimmt.|

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

## <a name="max_noneallocated"></a><a name="allocated"></a>max_none::zugeordnet

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

## <a name="max_nonedeallocated"></a><a name="deallocated"></a>max_none::deallocated

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

## <a name="max_nonefull"></a><a name="full"></a>max_none::voll

Gibt einen Wert zurück, der angibt, ob zur Freiliste weitere Speicherblöcke hinzugefügt werden sollen.

```cpp
bool full();
```

### <a name="return-value"></a>Rückgabewert

Diese Memberfunktion gibt immer **true**zurück.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird von `cache_freelist::deallocate` aufgerufen. Wenn der **true**Aufruf `deallocate` true zurückgibt, wird der Speicherblock in der freien Liste angezeigt. Wenn false **zurückgegeben**wird, `deallocate` ruft der Operator **delete** den Zuteilungsvorgang zurück.

## <a name="max_nonereleased"></a><a name="released"></a>max_none::veröffentlicht

Verringert die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void released();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Die `released`-Memberfunktion der aktuellen max-Klasse wird von `cache_freelist::allocate` aufgerufen, wann immer ein Speicherblock aus der Freiliste entfernt wird.

## <a name="max_nonesaved"></a><a name="saved"></a>max_none::gerettet

Erhöht die Anzahl der Speicherblöcke auf der Freiliste.

```cpp
void saved();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion bleibt untätig. Sie wird durch `cache_freelist::deallocate` aufgerufen, wann immer ein Speicherblock der Freiliste hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
