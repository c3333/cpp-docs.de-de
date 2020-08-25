---
title: Platform::Collections::UnorderedMap-Klasse
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: ec458f5d4a47b6eced939c4fe346d5d0414ea7c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839126"
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

*Km*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*V*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen. Standardmäßig [Std:: equal_to \<K> ](../standard-library/equal-to-struct.md).

### <a name="remarks"></a>Bemerkungen

Folgende Typen sind zulässig:

- integers

- Schnittstellen Klasse ^

- Öffentliche Referenzklasse^

- value struct

- Öffentliche Enumerationsklasse

**Unorderedmap** ist im Grunde ein Wrapper für [Std:: unordered_map](../standard-library/unordered-map-class.md) , der die Speicherung von Windows-Runtime Typen unterstützt. Dabei handelt es sich um eine konkrete Implementierung der Typen [Windows:: Foundation:: Collections:: IMap](/uwp/api/windows.foundation.collections.imap-2) und [iobservablemap](/uwp/api/windows.foundation.collections.iobservablemap-2) , die über öffentliche Windows-Runtime Schnittstellen übermittelt werden. Wenn Sie versuchen, einen `Platform::Collections::UnorderedMap` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder des Rückgabewerts auf [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)ändern.

Weitere Informationen finden Sie unter [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Unorderedmap:: unorderedmap](#ctor)|Initialisiert eine neue Instanz der Map-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Unorderedmap:: Clear](#clear)|Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.|
|[Unorderedmap:: First](#first)|Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt.|
|[Unorderedmap:: GetView](#getview)|Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; das heißt, eine Platform::Collections::UnorderedMapView-Klasse.|
|[Unorderedmap:: Haskey](#haskey)|Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.|
|[Unorderedmap:: INSERT](#insert)|Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.|
|[Unorderedmap:: Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen Map-Objekt ab.|
|[Unorderedmap:: Remove](#remove)|Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.|
|[Unorderedmap:: size](#size)|Gibt die Anzahl von Elementen im aktuellen Map-Objekt zurück.|

### <a name="events"></a>Ereignisse

| Name | Beschreibung |
|--|--|
| [Map:: mapchanged](#mapchanged) -Ereignis | Tritt auf, wenn sich die Map ändert. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`UnorderedMap`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a> Unorderedmap:: Clear-Methode

Entfernt alle Schlüssel-Wert-Paare aus dem aktuellen UnorderedMap-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a> Unorderedmap:: First-Methode

Gibt einen Iterator zurück, der das erste [Windows:: Foundation:: Collections:: ikeyvaluepair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) -Element in der ungeordneten Zuordnung angibt.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Zuordnung angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myUnorderedMap->First();`.

## <a name="unorderedmapgetview-method"></a><a name="getview"></a> Unorderedmap:: GetView-Methode

Gibt eine schreibgeschützte Ansicht der aktuellen unorderedmap zurück. Das heißt, eine [Platform:: Collections:: unorderedmapview-Klasse](../cppcx/platform-collections-unorderedmapview-class.md) , die die Schnittstelle [Windows:: Foundation:: Collections:: imapview:: imapview](/uwp/api/windows.foundation.collections.imapview-2) implementiert.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein `UnorderedMapView`-Objekt.

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a> Unorderedmap:: Haskey-Methode

Ermittelt, ob die aktuelle ungeordnete Zuordnung den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des UnorderedMap-Elements verwendete Schlüssel. Der *Schlüsseltyp* lautet Typname *K*.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Schlüssel gefunden wird. andernfalls **`false`** .

## <a name="unorderedmapinsert-method"></a><a name="insert"></a> Unorderedmap:: Insert-Methode

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
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* lautet Typname *K*.

*value*<br/>
Der Wertteil des Schlüssel-Wert-Paars. Der *Werttyp* ist Typname *V*.

### <a name="return-value"></a>Rückgabewert

**`true`** Wenn der Schlüssel eines vorhandenen Elements in der aktuellen Zuordnung mit *Key* übereinstimmt und der Wert Teil dieses Elements auf *value*festgelegt ist. **`false`** , wenn kein vorhandenes Element in der aktuellen Zuordnung mit *Key* übereinstimmt und die *Schlüssel* -und *Wert* Parameter in einem Schlüssel-Wert-Paar erstellt und dann der aktuellen unorderedmap hinzugefügt werden.

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a> Unorderedmap:: Lookup-Methode

Ruft den Wert des Typs V ab, der dem angegebenen Schlüssel des Typs K zugeordnet ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der UnorderedMap vorhandenen Elements verwendete Schlüssel. Der *Schlüsseltyp* lautet Typname *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der mit dem *Schlüssel*gekoppelt ist. Der Typ des Rückgabewerts ist Typname *V*.

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a> Unorderedmap:: mapchanged

Wird ausgelöst, wenn ein Element in eine Zuordnung eingefügt bzw. aus der Zuordnung entfernt wird.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [mapchangedeventhandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) , der Informationen zum Objekt enthält, das das Ereignis ausgelöst hat, sowie die Art der Änderung, die aufgetreten ist. Siehe auch [imapchangedebug \<K> ](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) -und [CollectionChange-Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework

Windows-Runtime apps, die c#-oder Visual Basic Project IMap \<K,V> als IDictionary verwenden \<K,V> .

## <a name="unorderedmapremove-method"></a><a name="remove"></a> Unorderedmap:: Remove-Methode

Löscht das angegebene Schlüssel-Wert-Paar vom UnorderedMap-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* lautet Typname *K*.

## <a name="unorderedmapsize-method"></a><a name="size"></a> Unorderedmap:: size-Methode

Gibt die Anzahl der [Windows:: Foundation:: Collections:: ikeyvaluepair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) -Elemente in der unorderedmap zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der ungeordneten Zuordnung.

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a> Unorderedmap:: unorderedmap-Konstruktor

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

*InIt*<br/>
Der Typname der aktuellen UnorderedMap.

*P*<br/>
Ein Funktionsobjekt, das zwei Schlüssel vergleichen kann, um zu bestimmen, ob sie gleich sind. Dieser Parameter ist standardmäßig [Std:: \<K> equal_to](../standard-library/equal-to-struct.md).

*H*<br/>
Ein Funktionsobjekt, das einen Hashwert für Schlüssel erzeugt. Dieser Parameter ist standardmäßig [Hash Class 1](../standard-library/hash-class.md) für die Schlüsseltypen, die von der-Klasse unterstützt werden.

*m*<br/>
Ein Verweis oder [Lvalues und Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) auf eine [Std:: unordered_map](../standard-library/unordered-map-class.md) , die verwendet wird, um die aktuelle unorderedmap zu initialisieren.

*Il*<br/>
Eine [Std:: initializer_list](../standard-library/initializer-list-class.md) von [Std::p Air](../standard-library/pair-structure.md) -Objekten, die zum Initialisieren der Zuordnung verwendet werden.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle UnorderedMap zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle UnorderedMap zu initialisieren.

## <a name="see-also"></a>Weitere Informationen

[Platform-Namespace](platform-namespace-c-cx.md)<br/>
[Platform:: Collections-Namespace](../cppcx/platform-collections-namespace.md)<br/>
[Platform:: Collections:: Map-Klasse](../cppcx/platform-collections-map-class.md)<br/>
[Platform:: Collections:: unorderedmapview-Klasse](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[Sammlungen](../cppcx/collections-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
