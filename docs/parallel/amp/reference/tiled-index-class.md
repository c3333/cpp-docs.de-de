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
ms.openlocfilehash: 9d295093031eaee0a2d4dd83aa931060e6eebc07
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832269"
---
# <a name="tiled_index-class"></a>tiled_index-Klasse

Stellt einen Index für ein [tiled_extent](tiled-extent-class.md) Objekt bereit. Diese Klasse verfügt über Eigenschaften, über die auf Elemente relativ zum lokalen Kachelursprung und relativ zum globalen Ursprung zugegriffen werden kann. Weitere Informationen zu gekachelten Leerzeichen finden [Sie unter Verwenden von Kacheln](../../../parallel/amp/using-tiles.md).

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

|name|Beschreibung|
|----------|-----------------|
|[tiled_index-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `tile_index`-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Gibt ein [Block](extent-class.md) Objekt zurück, das über die Werte der `tiled_index` Vorlagen Argumente `_Dim0` , und verfügt `_Dim1` `_Dim2` .|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|Beschreibung|
|----------|-----------------|
|[Barriere Konstante](#tiled_index__barrier)|Speichert ein [tile_barrier](tile-barrier-class.md) Objekt, das eine Barriere in der aktuellen Kachel der Threads darstellt.|
|[globale Konstante](#tiled_index__global)|Speichert ein [Index](index-class.md) Objekt von Rang 1, 2 oder 3, das den globalen Index in einem Raster Objekt darstellt.|
|[Lokale Konstante](#tiled_index__local)|Speichert ein `index` Objekt von Rang 1, 2 oder 3, das den relativen Index in der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.|
|[Rank-Konstante](#tiled_index__rank)|Speichert den Rang des `tiled_index`-Objekts.|
|[Kachel Konstante](#tiled_index__tile)|Speichert ein `index`-Objekt von Rang 1, 2 oder 3, das die Koordinaten der aktuellen Kachel eines `tiled_extent`-Objekts darstellt.|
|[tile_dim0 Konstante](#tiled_index__tile_dim0)|Speichert die Länge der wichtigsten Dimension.|
|[tile_dim1 Konstante](#tiled_index__tile_dim1)|Speichert die Länge der zweitwichtigsten Dimension.|
|[tile_dim2 Konstante](#tiled_index__tile_dim2)|Speichert die Länge der unwichtigsten Dimension.|
|[tile_origin Konstante](#tiled_index__tile_origin)|Speichert ein `index`-Objekt von Rang 1, 2 oder 3, das die globalen Koordinaten des Ursprungs der aktuellen Kachel in einem `tiled_extent`-Objekt darstellt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[tile_extent](#tile_extent)|Ruft ein [Block](extent-class.md) Objekt ab, das über die Werte der Vorlagen Argumente für Vorlagen Argumente `tiled_index` `tiled_index` `_Dim0` , `_Dim1` und verfügt `_Dim2` .|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp.h

**Namespace:** Parallelität

## <a name="tiled_index-constructor"></a><a name="ctor"></a> tiled_index-Konstruktor

Initialisiert eine neue Instanz der `tiled_index`-Klasse.

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
Der globale [Index](index-class.md) der erstellten `tiled_index` .

*_Local*<br/>
Der lokale [Index](index-class.md) der erstellten `tiled_index`

*_Tile*<br/>
Der Kachel [Index](index-class.md) des konstruierten `tiled_index`

*_Tile_origin*<br/>
Der Kachel Ursprungs [Index](index-class.md) des konstruierten `tiled_index`

*_Barrier*<br/>
Das [tile_barrier](tile-barrier-class.md) -Objekt der erstellten `tiled_index` .

*_Other*<br/>
Das `tile_index`-Objekt, das in das erstellte `tiled_index`-Objekt kopiert werden soll.

### <a name="overloads"></a>Überlädt

|Name|Beschreibung|
|-|-|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Initialisiert eine neue Instanz der `tile_index`-Klasse aus dem Index der Kachel in den globalen Koordinaten und der relativen Position in der Kachel in lokalen Koordinaten. Die Parameter `_Global` und `_Tile_origin` werden berechnet.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Initialisiert eine neue Instanz der `tile_index`-Klasse, indem das angegebene `tiled_index`-Objekt kopiert wird.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a> get_tile_extent

Gibt ein [Block](extent-class.md) Objekt zurück, das über die Werte der `tiled_index` Vorlagen Argumente `_Dim0` , und verfügt `_Dim1` `_Dim2` .

### <a name="syntax"></a>Syntax

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Ein `extent` -Objekt, das über die Werte der `tiled_index` Vorlagen Argumente `_Dim0` , und verfügt `_Dim1` `_Dim2` .

## <a name="barrier"></a><a name="tiled_index__barrier"></a> Barriere

Speichert ein [tile_barrier](tile-barrier-class.md) Objekt, das eine Barriere in der aktuellen Kachel der Threads darstellt.

### <a name="syntax"></a>Syntax

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a> Weltbühne

Speichert ein [Index](index-class.md) Objekt von Rang 1, 2 oder 3, das den globalen Index eines-Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a> nah

Speichert ein [Index](index-class.md) Objekt von Rang 1, 2 oder 3, das den relativen Index in der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a> gehören

Speichert den Rang des `tiled_index`-Objekts.

### <a name="syntax"></a>Syntax

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a> Stein

Speichert ein [Index](index-class.md) Objekt von Rang 1, 2 oder 3, das die Koordinaten der aktuellen Kachel eines [tiled_extent](tiled-extent-class.md) Objekts darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a> tile_dim0

Speichert die Länge der wichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a> tile_dim1

Speichert die Länge der zweitwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a> tile_dim2

Speichert die Länge der unwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a> tile_origin

Speichert ein [Index](index-class.md) Objekt von Rang 1, 2 oder 3, das die globalen Koordinaten des Ursprungs der aktuellen Kachel in einem [tiled_extent](tiled-extent-class.md) Objekt darstellt.

### <a name="syntax"></a>Syntax

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a> tile_extent

Ruft ein [Block](extent-class.md) Objekt ab, das über die Werte der Vorlagen Argumente für Vorlagen Argumente `tiled_index` `tiled_index` `_Dim0` , `_Dim1` und verfügt `_Dim2` .

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
