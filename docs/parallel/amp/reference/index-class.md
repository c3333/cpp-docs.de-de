---
title: index-Klasse
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365152"
---
# <a name="index-class"></a>index-Klasse

Definiert einen *N*N-dimensionalen Indexvektor.

## <a name="syntax"></a>Syntax

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>Parameter

*_Rank*<br/>
Der Rang oder die Anzahl von Dimensionen.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IndexKonstruktor](#index_ctor)|Initialisiert eine neue Instanz der Klasse `index`.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Betreiber--](#operator--)|Dekrementiert jedes Element des `index`-Objekts.|
|[Operator%=](#operator_mod_eq)|Berechnet den Modul (Rest) jedes Elements im `index`-Objekt, wenn dieses Element durch eine Zahl dividiert wird.|
|[Operator*=](#operator_star_eq)|Multipliziert jedes Element des `index`-Objekts mit einer Zahl.|
|[Operator/=](#operator_div_eq)|Dividiert jedes Element des `index`-Objekts durch eine Zahl.|
|[Index::Operator\[\]](#operator_at)|Gibt das Element am angegebenen Index zurück.|
|[Operator++](#operator_add_add)|Inkrementiert jedes Element des `index`-Objekts.|
|[Operator+=](#operator_add_eq)|Fügt die angegebene Zahl jedem Element des `index`-Objekts hinzu.|
|[Operator=](#operator_eq)|Kopiert den Inhalt des angegebenen `index`-Objekts in dieses Objekt.|
|[operator-=](#operator_-_eq)|Subtrahiert die angegebene Anzahl von jedem Element des `index`-Objekts.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Rang Konstante](#rank)|Speichert den Rang des `index`-Objekts.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`index`

## <a name="remarks"></a>Bemerkungen

Die `index` Struktur stellt einen Koordinatenvektor von *N-Ganzzahlen* dar, der eine eindeutige Position in einem *N-dimensionalen*Raum angibt. Die Werte im Vektor sind vom wichtigsten zum am wenigsten wichtigen Wert sortiert. Sie können die Werte der Komponenten mit [operator=](#operator_eq)abrufen.

## <a name="requirements"></a>Anforderungen

**Header:** amp.h

**Namespace:** Parallelität

## <a name="index-constructor"></a><a name="index_ctor"></a>IndexKonstruktor

Initialisiert eine neue Instanz der index-Klasse.

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Array*<br/>
Ein eindimensionales Array mit den Rangwerten.

*_I*<br/>
Die Indexposition in einem eindimensionalen Index.

*_I0*<br/>
Die Länge der wichtigsten Dimension.

*_I1*<br/>
Die Länge der zweitwichtigsten Dimension.

*_I2*<br/>
Die Länge der unwichtigsten Dimension.

*_Other*<br/>
Ein Indexobjekt, auf dem das neue Indexobjekt basiert.

## <a name="operator--"></a><a name="operator--"></a>Betreiber--

Dekrementiert jedes Element des index-Objekts.

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>Rückgabewerte

Für den Präfixoperator das Indexobjekt (*this). Für den Suffix-Operator ein neues Indexobjekt.

## <a name="operator"></a><a name="operator_mod_eq"></a>Operator%=

Berechnet den Modul (Rest) jedes Elements im Indexobjekt, wenn dieses Element durch die angegebene Zahl geteilt wird.

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Zahl, die geteilt werden soll, um den Modul zu finden.

## <a name="return-value"></a>Rückgabewert

Das Indexobjekt.

## <a name="operator"></a><a name="operator_star_eq"></a>Operator*=

Multipliziert jedes Element im index-Objekt mit der angegebenen Zahl.

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu multiplizierende Zahl.

## <a name="operator"></a><a name="operator_div_eq"></a>Operator/=

Dividiert jedes Element im Index-Objekt durch die angegebene Anzahl.

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Zahl, durch die dividiert wird.

## <a name="operator"></a><a name="operator_at"></a>Operator\[\]

Gibt die Komponente des Index an der angegebenen Position zurück.

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Index*<br/>
Eine ganze Zahl von 0 durch den Rang minus 1.

### <a name="return-value"></a>Rückgabewert

Das Element am angegebenen Index.

### <a name="remarks"></a>Bemerkungen

Im folgenden Beispiel werden die Komponentenwerte des Index angezeigt.

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>Operator++

Inkrementiert jedes Element des index-Objekts.

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>Rückgabewert

Für den Präfixoperator das Indexobjekt (*this). Für den Suffix-Operator ein neues Indexobjekt.

## <a name="operator"></a><a name="operator_add_eq"></a>Operator+=

Fügt die angegebene Zahl jedem Element des Index-Objekts hinzu.

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die hinzuzufügende Zahl.

### <a name="return-value"></a>Rückgabewert

Das Indexobjekt.

## <a name="operator"></a><a name="operator_eq"></a>Operator=

Kopiert den Inhalt des angegebenen index-Objekts in dieses Objekt.

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das Indexobjekt, aus dem kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf dieses Indexobjekt.

## <a name="operator-"></a><a name="operator_-_eq"></a>operator-=

Subtrahiert die angegebene Anzahl von jedem Element des index-Objekts.

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die zu subtrahierende Zahl.

### <a name="return-value"></a>Rückgabewert

Das Indexobjekt.

## <a name="rank"></a><a name="rank"></a>Rang

Ruft den Rang des Indexobjekts ab.

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>Siehe auch

[Parallelitätsnamespace (C++ AMP)](concurrency-namespace-cpp-amp.md)
