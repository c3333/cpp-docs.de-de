---
title: Platform::Collections::MapView-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 693854499dafd23752337652ef298907fdecbcc2
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610893"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView-Klasse

Stellt eine schreibgeschützte Ansicht einer *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist.

## <a name="syntax"></a>Syntax

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>Parameter

*Km*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*Ramelow*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der MapView zu bestimmen. Standardmäßig ist dies [Std:: \<K> less](../standard-library/less-struct.md).

### <a name="remarks"></a>Hinweise

MapView ist eine konkrete C++-Implementierung der [Windows:: Foundation:: Collections:: imapview \<K,V> ](/uwp/api/windows.foundation.collections.imapview-2) -Schnittstelle, die über die Anwendungs Binärdatei Schnittstelle (ABI) übergeben wird. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[MapView:: MapView](#ctor)|Initialisiert eine neue Instanz der MapView-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[MapView:: First](#first)|Gibt einen Iterator zurück, der mit dem ersten Element der Zuordnungsansicht initialisiert wird.|
|[MapView:: Haskey](#haskey)|Ermittelt, ob die aktuelle MapView den angegebenen Schlüssel enthält.|
|[MapView:: Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen MapView-Objekt ab.|
|[MapView::Size](#size)|Gibt die Anzahl von Elementen im aktuellen MapView-Objekt zurück.|
|[MapView:: Split](#split)|Teilt ein Original-MapView-Objekt in zwei MapView-Objekte.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`MapView`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a> MapView:: First-Methode

Gibt einen Iterator zurück, der das erste Element in der Kartenansicht angibt.

### <a name="syntax"></a>Syntax

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Kartenansicht angibt.

### <a name="remarks"></a>Hinweise

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myMapView->First();`.

## <a name="mapviewhaskey-method"></a><a name="haskey"></a> MapView:: Haskey-Methode

Ermittelt, ob die aktuelle MapView den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```

bool HasKey(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des MapView-Elements verwendete Schlüssel. Der *Schlüsseltyp* lautet Typname *K*.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Schlüssel gefunden wird. andernfalls **`false`** .

## <a name="mapviewlookup-method"></a><a name="lookup"></a> MapView:: Lookup-Methode

Ruft den Wert des Typs V ab, der dem angegebenen Schlüssel des Typs K zugeordnet ist.

### <a name="syntax"></a>Syntax

```
V Lookup(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der MapView vorhandenen Elements verwendete Schlüssel. Der Typ von `key` ist Typname *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der dem `key` zugeordnet ist. Der Typ des Rückgabewerts ist Typname *V*.

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a> MapView:: MapView-Konstruktor

Initialisiert eine neue Instanz der MapView-Klasse.

### <a name="syntax"></a>Syntax

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>Parameter

*InIt*<br/>
Der Typname der aktuellen MapView.

*comp*<br/>
Ein Funktionsobjekt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der MapView zu bestimmen.

*m*<br/>
Ein Verweis oder [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) für einen `map Class` , der verwendet wird, um die aktuelle MapView zu initialisieren.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle MapView zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle MapView zu initialisieren.

*Il*<br/>
Eine [Std:: initializer_list \<std::pair\<K,V> > ](../standard-library/initializer-list-class.md) , deren Elemente in die MapView eingefügt werden.

## <a name="mapviewsize-method"></a><a name="size"></a> MapView:: size-Methode

Gibt die Anzahl von Elementen im aktuellen MapView-Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in der aktuellen MapView.

## <a name="mapviewsplit-method"></a><a name="split"></a> MapView:: Split-Methode

Teilt das aktuelle MapView-Objekt in zwei MapView-Objekte. Diese Methode führt keine Operationen aus.

### <a name="syntax"></a>Syntax

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>Parameter

*firstpartition*<br/>
Der erste Teil des ursprünglichen MapView-Objekts.

*secondpartition*<br/>
Der zweite Teil des ursprünglichen MapView-Objekts.

### <a name="remarks"></a>Hinweise

Diese Methode führt keine Operationen aus und hat keine Auswirkungen.

## <a name="see-also"></a>Siehe auch

[Platform-Namespace](platform-namespace-c-cx.md)
