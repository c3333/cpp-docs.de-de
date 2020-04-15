---
title: tiled_index-Klasse
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375482"
---
# <a name="tiled_index-class"></a>tiled_index-Klasse

Stellt einen Index für ein [tiled_extent-Objekt](tiled-extent-class.md) bereit. Diese Klasse verfügt über Eigenschaften, über die auf Elemente relativ zum lokalen Kachelursprung und relativ zum globalen Ursprung zugegriffen werden kann. Weitere Informationen zu gekachelten Räumen finden Sie unter [Verwenden von Kacheln](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Syntax

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>Parameter

*_Dim0*<br/>
Die Länge der wichtigsten Dimension.

*_Dim1*<br/>
Die Länge der zweitwichtigsten Dimension.

*_Dim2*<br/>
Die Länge der unwichtigsten Dimension.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[tiled_index Konstruktor](#ctor)|Initialisiert eine neue Instanz der Klasse `tile_index`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Gibt ein [Ausdehnungsobjekt](extent-class.md) zurück, `_Dim0`das `_Dim1`die `_Dim2`Werte der `tiled_index` Vorlagenargumente , und enthält.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Barriere Konstante](#tiled_index__barrier)|Speichert ein [tile_barrier](tile-barrier-class.md) Objekt, das eine Barriere in der aktuellen Kachel von Threads darstellt.|
|||
|[globale Konstante](#tiled_index__global)|Speichert ein [Indexobjekt](index-class.md) von Rang 1, 2 oder 3, das den globalen Index in einem Rasterobjekt darstellt.|
|[Lokale Konstante](#tiled_index__local)|Speichert `index` ein Objekt von Rang 1, 2 oder 3, das den relativen Index in der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.|
|[Rang Konstante](#tiled_index__rank)|Speichert den Rang des `tiled_index`-Objekts.|
|[Fliesen konstante](#tiled_index__tile)|Speichert ein `index`-Objekt von Rang 1, 2 oder 3, das die Koordinaten der aktuellen Kachel eines `tiled_extent`-Objekts darstellt.|
|[tile_dim0 Constant](#tiled_index__tile_dim0)|Speichert die Länge der wichtigsten Dimension.|
|[tile_dim1 Constant](#tiled_index__tile_dim1)|Speichert die Länge der zweitwichtigsten Dimension.|
|[tile_dim2 Constant](#tiled_index__tile_dim2)|Speichert die Länge der unwichtigsten Dimension.|
|[tile_origin Constant](#tiled_index__tile_origin)|Speichert ein `index`-Objekt von Rang 1, 2 oder 3, das die globalen Koordinaten des Ursprungs der aktuellen Kachel in einem `tiled_extent`-Objekt darstellt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[tile_extent](#tile_extent)|Ruft ein [Ausdehnungsobjekt](extent-class.md) ab, das die `_Dim1`Werte `_Dim2` `tiled_index` der Vorlagenargumente `tiled_index` Vorlagenargumente `_Dim0`, und enthält.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Anforderungen

**Header:** amp.h

**Namespace:** Parallelität

## <a name="tiled_index-constructor"></a><a name="ctor"></a>tiled_index Konstruktor

Initialisiert eine neue Instanz der Klasse `tiled_index`.

### <a name="syntax"></a>Syntax

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Global*<br/>
Der globale [Index](index-class.md) `tiled_index`der konstruierten .

*_Local*<br/>
Der lokale [Index](index-class.md) der konstruierten`tiled_index`

*_Tile*<br/>
Der [Kachelindex](index-class.md) des konstruierten`tiled_index`

*_Tile_origin*<br/>
Der [Kachelursprungsindex](index-class.md) des konstruierten`tiled_index`

*_Barrier*<br/>
Das [tile_barrier](tile-barrier-class.md) Objekt `tiled_index`der konstruierten .

*_Other*<br/>
Das `tile_index`-Objekt, das in das erstellte `tiled_index`-Objekt kopiert werden soll.

### <a name="overloads"></a>Overloads

|||
|-|-|
|Name|BESCHREIBUNG|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Initialisiert eine neue Instanz der `tile_index`-Klasse aus dem Index der Kachel in den globalen Koordinaten und der relativen Position in der Kachel in lokalen Koordinaten. Die Parameter `_Global` und `_Tile_origin` werden berechnet.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Initialisiert eine neue Instanz der `tile_index`-Klasse, indem das angegebene `tiled_index`-Objekt kopiert wird.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

Gibt ein [Ausdehnungsobjekt](extent-class.md) zurück, `_Dim0`das `_Dim1`die `_Dim2`Werte der `tiled_index` Vorlagenargumente , und enthält.

### <a name="syntax"></a>Syntax

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Ein `extent` Objekt mit den `tiled_index` Werten `_Dim0`der `_Dim1`Vorlagenargumente , und `_Dim2`.

## <a name="barrier"></a><a name="tiled_index__barrier"></a>Barriere

Speichert ein [tile_barrier](tile-barrier-class.md) Objekt, das eine Barriere in der aktuellen Kachel von Threads darstellt.

### <a name="syntax"></a>Syntax

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>Globalen

Speichert ein [Indexobjekt](index-class.md) von Rang 1, 2 oder 3, das den globalen Index eines Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>lokal

Speichert ein [Indexobjekt](index-class.md) von Rang 1, 2 oder 3, das den relativen Index in der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>Rang

Speichert den Rang des `tiled_index`-Objekts.

### <a name="syntax"></a>Syntax

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>Fliese

Speichert ein [Indexobjekt](index-class.md) von Rang 1, 2 oder 3, das die Koordinaten der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

Speichert die Länge der wichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

Speichert die Länge der zweitwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

Speichert die Länge der unwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

Speichert ein [Indexobjekt](index-class.md) von Rang 1, 2 oder 3, das die globalen Koordinaten des Ursprungs der aktuellen Kachel in einem [tiled_extent](tiled-extent-class.md) Objekt darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

Ruft ein [Ausdehnungsobjekt](extent-class.md) ab, das die `_Dim1`Werte `_Dim2` `tiled_index` der Vorlagenargumente `tiled_index` Vorlagenargumente `_Dim0`, und enthält.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
