---
title: Platform::Collections::UnorderedMapView-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: acfc168959deb83244c98c5d361cf9e73c1388f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213059"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView-Klasse

Stellt eine schreibgeschützte Ansicht einer *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist.

## <a name="syntax"></a>Syntax

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>Parameter

*Km*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*Ramelow*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Schlüsselwerte vergleichen kann, um deren Gleichzeit zu bestimmen. Standardmäßig [Std:: equal_to \<K> ](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>Bemerkungen

Unorderedmapview ist eine konkrete C++-Implementierung der [Windows:: Foundation:: Collections:: imapview \<K,V> ](/uwp/api/windows.foundation.collections.imapview-2) -Schnittstelle, die über die Anwendungs Binärdatei Schnittstelle (ABI) übergeben wird. Weitere Informationen finden Sie unter [Auflistungen (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Unorderedmapview:: unorderedmapview](#ctor)|Initialisiert eine neue Instanz der UnorderedMapView-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Unorderedmapview:: First](#first)|Gibt einen Iterator zurück, der mit dem ersten Element der Zuordnungsansicht initialisiert wird.|
|[Unorderedmapview:: Haskey](#haskey)|Ermittelt, ob die aktuelle UnorderedMapView den angegebenen Schlüssel enthält.|
|[Unorderedmapview:: Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen UnorderedMapView-Objekt ab.|
|[Unorderedmapview:: size](#size)|Gibt die Anzahl von Elementen im aktuellen UnorderedMapView-Objekt zurück.|
|[Unorderedmapview:: Split](#split)|Teilt ein originales UnorderedMapView-Objekt in zwei UnorderedMapView-Objekte.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`UnorderedMapView`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>Unorderedmapview:: First-Methode

Gibt einen Iterator zurück, der das erste [Windows:: Foundation:: Collections:: ikeyvaluepair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) -Element in der ungeordneten Zuordnung angibt.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Kartenansicht angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myMapView->First();`.

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>Unorderedmapview:: Haskey-Methode

Ermittelt, ob die aktuelle ungeordnete Zuordnung den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des Elements verwendete Schlüssel. Der Typ von `key` ist Typname *K*.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der Schlüssel gefunden wird. andernfalls **`false`** .

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>Unorderedmapview:: Lookup-Methode

Ruft den Wert des Typs V ab, der dem angegebenen Schlüssel des Typs K zugeordnet ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der UnorderedMapView vorhandenen Elements verwendete Schlüssel. Der Typ von `key` ist Typname *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der dem `key` zugeordnet ist. Der Typ des Rückgabewerts ist Typname *V*.

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>Unorderedmapview:: size-Methode

Gibt die Anzahl der [Windows:: Foundation:: Collections:: ikeyvaluepair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) -Elemente in der unorderedmapview zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der UnorderedMapView.

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>Unorderedmapview:: Split-Methode

Teilt das aktuelle UnorderedMapView-Objekt in zwei UnorderedMapView-Objekte. Diese Methode führt keine Operationen aus.

### <a name="syntax"></a>Syntax

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>Parameter

*firstpartition*<br/>
Der erste Teil des ursprünglichen UnorderedMapView-Objekts.

*secondpartition*<br/>
Der zweite Teil des ursprünglichen UnorderedMapView-Objekts.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt keine Operationen aus und hat keine Auswirkungen.

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>Unorderedmapview:: unorderedmapview-Konstruktor

Initialisiert eine neue Instanz der UnorderedMapView-Klasse.

### <a name="syntax"></a>Syntax

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>Parameter

*n*<br/>
Die Anzahl der Elemente, für die Speicherplatz vorab zugewiesen werden soll.

*InIt*<br/>
Der Typname der UnorderedMapView.

*H*<br/>
Ein Funktionsobjekt, das einen Hashwert für einen Schlüssel haben kann. Der Standardwert ist [Std: \<K> : Hash](../standard-library/hash-class.md) für die Typen, die von `std::hash` unterstützt werden.

*P*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Schlüssel vergleichen kann, um deren Gleichheit zu bestimmen. Der Standardwert ist [Std: \<K> : equal_to](../standard-library/equal-to-struct.md).

*m*<br/>
Ein Verweis oder [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) auf eine [Std:: unordered_map](../standard-library/unordered-map-class.md) , die verwendet wird, um die unorderedmapview zu initialisieren.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die UnorderedMapView zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die UnorderedMapView zu initialisieren.

## <a name="see-also"></a>Weitere Informationen

[Platform:: Collections-Namespace](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
