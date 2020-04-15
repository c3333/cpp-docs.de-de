---
title: Platform::Collections::UnorderedMap-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354422"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap-Klasse

Stellt eine ungeordnete *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist.

## <a name="syntax"></a>Syntax

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>Parameter

*K*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*V*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen. Standardmäßig [ist\<std::equal_to K>](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Bemerkungen

Folgende Typen sind zulässig:

- Ganze Zahlen

- Schnittstellenklasse

- Öffentliche Referenzklasse^

- value struct

- Öffentliche Enumerationsklasse

**UnorderedMap** ist im Grunde ein Wrapper für [std::unordered_map,](../standard-library/unordered-map-class.md) der die Speicherung von Windows-Runtime-Typen unterstützt. Es ist die konkrete Implementierung der [Windows::Foundation::Collections::IMap-](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) und [IObservableMap-Typen,](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) die über öffentliche Windows-Runtime-Schnittstellen übergeben werden. Wenn Sie versuchen, einen `Platform::Collections::UnorderedMap` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder des Rückgabewerts auf [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)ändern.

Weitere Informationen finden Sie unter [Sammlungen](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|Initialisiert eine neue Instanz der Map-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[UnorderedMap::Löschen](#clear)|Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.|
|[UnorderedMap::Erste](#first)|Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt.|
|[UngeordneteKarte::GetView](#getview)|Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; das heißt, eine Platform::Collections::UnorderedMapView-Klasse.|
|[UngeordneteKarte::HasKey](#haskey)|Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.|
|[UnorderedMap::Einfügen](#insert)|Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.|
|[UngeordneteKarte::Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen Map-Objekt ab.|
|[UnorderedMap::Entfernen](#remove)|Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.|
|[UnorderedMap::Größe](#size)|Gibt die Anzahl von Elementen im aktuellen Map-Objekt zurück.|

### <a name="events"></a>Ereignisse

|||
|-|-|
|Name|BESCHREIBUNG|
|[Karte::MapChanged-Ereignis](#mapchanged)|Tritt auf, wenn sich die Map ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`UnorderedMap`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap::Clear-Methode

Entfernt alle Schlüssel-Wert-Paare aus dem aktuellen UnorderedMap-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap::Erste Methode

Gibt einen Iterator zurück, der das erste [Windows::Foundation::Collections::IKeyValuePair\<K,V->-Element](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) in der ungeordneten Karte angibt.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Zuordnung angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First() zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird. Beispiel: `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap::GetView-Methode

Gibt eine schreibgeschützte Ansicht der aktuellen UnorderedMap zurück. Das heißt, eine [Platform::Collections::UnorderedMapView-Klasse,](../cppcx/platform-collections-unorderedmapview-class.md) die die Schnittstelle [Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) implementiert.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein `UnorderedMapView`-Objekt.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap::HasKey-Methode

Ermittelt, ob die aktuelle ungeordnete Zuordnung den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des UnorderedMap-Elements verwendete Schlüssel. Der *Schlüsseltyp* ist der TypName *K*.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Schlüssel gefunden wird; andernfalls **false**.

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap::Insert-Methode

Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen UnorderedMap-Objekt hinzu.

### <a name="syntax"></a>Syntax

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* ist der TypName *K*.

*value*<br/>
Der Wertteil des Schlüssel-Wert-Paars. Der *Werttyp* ist typname *V*.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Schlüssel eines vorhandenen Elements in der aktuellen Karte mit dem *Schlüssel* übereinstimmt und der Wertteil dieses Elements auf *Wert*festgelegt ist. **false,** wenn kein vorhandenes Element in der aktuellen Karte mit dem *Schlüssel* übereinstimmt und die *Schlüssel-* und *Wertparameter* zu einem Schlüssel-Wert-Paar gemacht und dann der aktuellen UnorderedMap hinzugefügt werden.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap::Lookup-Methode

Ruft den Wert des Typs V ab, der dem angegebenen Schlüssel des Typs K zugeordnet ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der UnorderedMap vorhandenen Elements verwendete Schlüssel. Der *Schlüsseltyp* ist der TypName *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der mit dem *Schlüssel*gekoppelt ist. Der Typ des Rückgabewerts ist der Typname *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UngeordneteKarte::MapChanged

Wird ausgelöst, wenn ein Element in eine Zuordnung eingefügt bzw. aus der Zuordnung entfernt wird.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler) der Informationen über das Objekt enthält, das das Ereignis ausgelöst hat, und die Art der Änderungen, die aufgetreten sind. Siehe auch [IMapChangedEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) und [CollectionChange Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework

Windows-Runtime-Apps, die wir mit\<dem Projekt IMap\<K,V> als IDictionary K,V>.

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap::Remove-Methode

Löscht das angegebene Schlüssel-Wert-Paar vom UnorderedMap-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* ist der TypName *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap::Size-Methode

Gibt die Anzahl von [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) Elementen in der UnorderedMap zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der ungeordneten Zuordnung.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap::UnorderedMap Konstruktor

Initialisiert eine neue Instanz der UnorderedMap-Klasse.

### <a name="syntax"></a>Syntax

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>Parameter

*Init*<br/>
Der Typname der aktuellen UnorderedMap.

*P*<br/>
Ein Funktionsobjekt, das zwei Schlüssel vergleichen kann, um zu bestimmen, ob sie gleich sind. Dieser Parameter ist standardmäßig [\<std::equal_to K>](../standard-library/equal-to-struct.md).

*H*<br/>
Ein Funktionsobjekt, das einen Hashwert für Schlüssel erzeugt. Dieser Parameter ist standardmäßig [Hashklasse 1](../standard-library/hash-class.md) für die von der Klasse unterstützten Schlüsseltypen.

*M*<br/>
Ein Verweis oder [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) auf eine [std::unordered_map,](../standard-library/unordered-map-class.md) die zum Initialisieren der aktuellen UnorderedMap verwendet wird.

*Il*<br/>
Eine [std::initializer_list](../standard-library/initializer-list-class.md) von [std::pair-Objekten,](../standard-library/pair-structure.md) die zum Initialisieren der Karte verwendet werden.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle UnorderedMap zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle UnorderedMap zu initialisieren.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Platform::Collections-Namespace](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map-Klasse](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView-Klasse](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Sammlungen](../cppcx/collections-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
