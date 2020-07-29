---
title: extent-Klasse (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: b9fd0ffb0c3ac6e0b80823e9f31c3615a045262b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222731"
---
# <a name="extent-class-c-amp"></a>extent-Klasse (C++ AMP)

Stellt einen Vektor von *n* ganzzahligen Werten dar, die die Begrenzungen eines *n*-dimensionalen Raums mit dem Ursprung 0 angeben. Die Werte im Vektor sind vom wichtigsten zum am wenigsten wichtigen Wert sortiert.

## <a name="syntax"></a>Syntax

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang des `extent`-Objekts.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp.h

**Namespace:** Parallelität

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Block-Konstruktor](#ctor)|Initialisiert eine neue Instanz der `extent`-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[contains](#contains)|Überprüft, ob das angegebene `extent`-Objekt über den angegebenen Rang verfügt.|
|[size](#size)|Gibt die lineare Gesamtgröße des Wertebereichs zurück (in der Einheit Elemente).|
|[tile](#tile)|Erzeugt ein `tiled_extent`-Objekt mit den Kachelwertebereichen, die durch angegebene Dimensionen festgelegt werden.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[KOM](#operator_min)|Gibt ein neues `extent`-Objekt zurück, das erstellt wird, indem die `index`-Elemente von den entsprechenden `extent`-Elementen subtrahiert werden.|
|[Operator--](#operator_min_min)|Dekrementiert jedes Element des `extent`-Objekts.|
|[Operator% =](#operator_mod_eq)|Berechnet den Modul (Rest) jedes Elements im `extent`-Objekt, wenn dieses Element durch eine Zahl dividiert wird.|
|[Operator * =](#operator_star_eq)|Multipliziert jedes Element des `extent`-Objekts mit einer Zahl.|
|[Operator/=](#operator_min_eq)|Dividiert jedes Element des `extent`-Objekts durch eine Zahl.|
|[Block::-Operator\[\]](#operator_at)|Gibt das Element am angegebenen Index zurück.|
|[Operator +](#operator_add)|Gibt ein neues `extent`-Objekt zurück, das durch Hinzufügen der entsprechenden `index`- und `extent`-Elemente erstellt wird.|
|[Operator + +](#operator_add_add)|Inkrementiert jedes Element des `extent`-Objekts.|
|[Operator + =](#operator_add_eq)|Fügt die angegebene Zahl jedem Element des `extent`-Objekts hinzu.|
|[Operator =](#operator_eq)|Kopiert den Inhalt eines anderen `extent`-Objekts in dieses Objekt.|
|[Operator-=](#operator_min_eq)|Subtrahiert die angegebene Anzahl von jedem Element des `extent`-Objekts.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Rank-Konstante](#rank_constant)|Ruft den Rang des `extent`-Objekts ab.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`extent`

## <a name="contains"></a><a name="contains"></a>Inhalt

Gibt an, ob der angegebene [Indexwert](index-class.md) im ' Block '-Objekt enthalten ist.

### <a name="syntax"></a>Syntax

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Index*<br/>
Der zu testende `index`-Wert.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der angegebene *Indexwert* im- `extent` Objekt enthalten ist, andernfalls **`false`** .

## <a name="extent"></a><a name="ctor"></a>Ausdehnung

Initialisiert eine neue Instanz der "Block"-Klasse.

### <a name="syntax"></a>Syntax

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Array*<br/>
Ein Array mit ganzen `_Rank`-Zahlen, mit dem das neue `extent`-Objekt erstellt wird.

*_I*<br/>
Die Länge des Wertebereichs.

*_I0*<br/>
Die Länge der wichtigsten Dimension.

*_I1*<br/>
Die Länge der zweitwichtigsten Dimension.

*_I2*<br/>
Die Länge der unwichtigsten Dimension.

*_Other*<br/>
Ein `extent`-Objekt, auf dem das neue `extent`-Objekt basiert.

## <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor initialisiert ein- `extent` Objekt, das den Rang drei hat.

Wenn ein Array verwendet wird, um ein `extent`-Objekt zu erstellen, muss die Länge des Arrays mit dem Rang des `extent`-Objekts übereinstimmen.

## <a name="operator"></a><a name="operator_mod_eq"></a>Operator% =

Berechnet den Modulo (Rest) jedes Elements im ' Block ', wenn dieses Element durch eine Zahl dividiert wird.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Zahl, für die der Modulo gefunden werden soll.

### <a name="return-value"></a>Rückgabewert

Das `extent`-Objekt.

## <a name="operator"></a><a name="operator_star_eq"></a>Operator * =

Multipliziert jedes Element im ' Block '-Objekt mit der angegebenen Zahl.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu multiplizierende Zahl.

### <a name="return-value"></a>Rückgabewert

Das `extent`-Objekt.

## <a name="operator"></a><a name="operator_add"></a>Operator +

Gibt ein neues `extent`-Objekt zurück, das durch Hinzufügen der entsprechenden `index`- und `extent`-Elemente erstellt wird.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Das `index`-Objekt, das die hinzuzufügenden Elemente enthält.

### <a name="return-value"></a>Rückgabewert

Das neue `extent`-Objekt.

## <a name="operator"></a><a name="operator_add_add"></a>Operator + +

Inkremente jedes Element des "Block"-Objekts.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Für den Prefix-Operator das- `extent` Objekt ( **`*this`** ). Für den Suffixoperator ein neues `extent`-Objekt.

## <a name="operator"></a><a name="operator_add_eq"></a>Operator + =

Fügt die angegebene Zahl jedem Element des Block-Objekts hinzu.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Zahl, der Index oder der Wertebereich, die bzw. der hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Das resultierende `extent`-Objekt.

## <a name="operator-"></a><a name="operator_min"></a>KOM

Erstellt ein neues `extent`-Objekt durch Subtrahieren der einzelnen Elemente im angegebenen `index`-Objekt vom entsprechenden Element in diesem `extent`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Das `index`-Objekt, das die zu subtrahierenden Elemente enthält.

### <a name="return-value"></a>Rückgabewert

Das neue `extent`-Objekt.

## <a name="operator--"></a><a name="operator_min_min"></a>Operator--

Dekremente jedes Element im ' Block '-Objekt.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Für den Prefix-Operator das- `extent` Objekt ( **`*this`** ). Für den Suffixoperator ein neues `extent`-Objekt.

## <a name="operator"></a><a name="operator_div_eq"></a>Operator/=

Dividiert jedes Element im ' Block '-Objekt durch die angegebene Zahl.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Zahl, durch die dividiert wird.

### <a name="return-value"></a>Rückgabewert

Das `extent`-Objekt.

## <a name="operator-"></a><a name="operator_min_eq"></a>Operator-=

Subtrahiert die angegebene Zahl von jedem Element des "Block"-Objekts.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu subtrahierende Zahl.

### <a name="return-value"></a>Rückgabewert

Das resultierende `extent`-Objekt.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Kopiert den Inhalt eines anderen ' Block '-Objekts in dieses Objekt.

### <a name="syntax"></a>Syntax

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `extent`-Objekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `extent`-Objekt.

## <a name="extentoperator-"></a><a name="operator_at"></a>Block::-Operator\[\]

Gibt das Element am angegebenen Index zurück.

### <a name="syntax"></a>Syntax

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Index*<br/>
Eine ganze Zahl von 0 durch den Rang minus 1.

### <a name="return-value"></a>Rückgabewert

Das Element am angegebenen Index.

## <a name="rank"></a><a name="rank_constant"></a>gehören

Speichert den Rang des ' Block '-Objekts.

### <a name="syntax"></a>Syntax

```cpp
static const int rank = _Rank;
```

## <a name="size"></a><a name="size"></a>Größe

Gibt die gesamte lineare Größe des- `extent` Objekts zurück (in Einheiten von Elementen).

### <a name="syntax"></a>Syntax

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a><a name="tile"></a>Stein

Erzeugt ein tiled_extent-Objekt mit den angegebenen Kacheldimensionen.

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>Parameter

*_Dim0*<br/>
Die wichtigste Komponente des unterteilten Wertebereichs.
*_Dim1*<br/>
Die zweitwichtigste Komponente des unterteilten Wertebereichs.
*_Dim2*<br/>
Die unwichtigste Komponente des unterteilten Wertebereichs.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)
