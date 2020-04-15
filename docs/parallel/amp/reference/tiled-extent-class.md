---
title: tiled_extent-Klasse
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374714"
---
# <a name="tiled_extent-class"></a>tiled_extent-Klasse

Ein `tiled_extent`-Objekt ist ein `extent`-Objekt einer bis drei Dimensionen, das den "extent"-Bereich in ein-, zwei- oder dreidimensionale Kacheln unterteilt.

## <a name="syntax"></a>Syntax

```cpp
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
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
|[tiled_extent Konstrukteur](#ctor)|Initialisiert eine neue Instanz der Klasse `tiled_extent`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Gibt ein `extent`-Objekt zurück, das die Werte der `tiled_extent`-Vorlagenargumente `_Dim0`, `_Dim1` und `_Dim2` erfasst.|
|[Pad](#pad)|Gibt ein neues `tiled_extent`-Objekt mit den Wertebereichen zurück, die aufgerundet werden, um durch die Kacheldimensionen teilbar zu sein.|
|[truncate](#truncate)|Gibt ein neues `tiled_extent`-Objekt mit den Wertebereichen zurück, die abgerundet werden, um durch die Kacheldimensionen teilbar zu sein.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator=](#operator_eq)|Kopiert den Inhalt des angegebenen `tiled_index`-Objekts in dieses Objekt.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[tile_dim0 Constant](#tile_dim0)|Speichert die Länge der wichtigsten Dimension.|
|[tile_dim1 Constant](#tile_dim1)|Speichert die Länge der zweitwichtigsten Dimension.|
|[tile_dim2 Constant](#tile_dim2)|Speichert die Länge der unwichtigsten Dimension.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[tile_extent](#tile_extent)|Ruft ein `extent`-Objekt ab, das die Werte der `tiled_extent`-Vorlagenargumente `_Dim0`, `_Dim1` und `_Dim2` erfasst.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`extent`

`tiled_extent`

## <a name="requirements"></a>Anforderungen

**Header:** amp.h

**Namespace:** Parallelität

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> tiled_extent Konstruktor

Initialisiert eine neue Instanz der Klasse `tiled_extent`.

### <a name="syntax"></a>Syntax

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `extent`- oder `tiled_extent`-Objekt, in das kopiert werden soll.

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

Gibt `extent` ein Objekt zurück, das `tiled_extent` die `_Dim0` `_Dim1`Werte `_Dim2`der Vorlagenargumente , und erfasst.

### <a name="syntax"></a>Syntax

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Ein `extent`-Objekt, das die Dimensionen dieser `tiled_extent`-Instanz erfasst.

## <a name="pad"></a><a name="pad"> </a> Pad

Gibt ein neues `tiled_extent`-Objekt mit den Wertebereichen zurück, die aufgerundet werden, um durch die Kacheldimensionen teilbar zu sein.

### <a name="syntax"></a>Syntax

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Rückgabewert

Das neue `tiled_extent`-Objekts, nach Wert.

## <a name="truncate"></a><a name="truncate"> </a> abschneiden

Gibt ein neues `tiled_extent`-Objekt mit den Wertebereichen zurück, die abgerundet werden, um durch die Kacheldimensionen teilbar zu sein.

### <a name="syntax"></a>Syntax

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt ein neues `tiled_extent`-Objekt mit den Wertebereichen zurück, die abgerundet werden, um durch die Kacheldimensionen teilbar zu sein.

## <a name="operator"></a><a name="operator_eq"> </a> Operator=

Kopiert den Inhalt des angegebenen `tiled_index`-Objekts in dieses Objekt.

### <a name="syntax"></a>Syntax

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `tiled_index`-Objekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf diese `tiled_index`-Instanz.

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

Speichert die Länge der wichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

Speichert die Länge der zweitwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

Speichert die Länge der unwichtigsten Dimension.

### <a name="syntax"></a>Syntax

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

Ruft `extent` ein Objekt ab, das `tiled_extent` die `_Dim0` `_Dim1`Werte `_Dim2`der Vorlagenargumente , und erfasst.

### <a name="syntax"></a>Syntax

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
