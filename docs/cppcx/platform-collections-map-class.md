---
title: Platform::Collections::Map-Klasse
ms.date: 10/01/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 0ddb15507c97c0dfff48575e476b57fe91359239
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610906"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map-Klasse

Stellt eine *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist. Implementiert [Windows:: Foundation:: Collections:: iobservablemap](/uwp/api/windows.foundation.collections.iobservablemap-2) , um die XAML- [Datenbindung](/windows/uwp/data-binding/data-binding-in-depth)zu unterstützen.

## <a name="syntax"></a>Syntax

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parameter

*Km*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*Ramelow*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen. Standardmäßig ist dies [Std:: \<K> less](../standard-library/less-struct.md).

*__is_valid_winrt_type ()* Eine vom Compiler generierte Funktion, die den Typ von *K* und *V* überprüft und eine benutzerfreundliche Fehlermeldung bereitstellt, wenn der Typ nicht in der Zuordnung gespeichert werden kann.

### <a name="remarks"></a>Hinweise

Folgende Typen sind zulässig:

- integers

- Schnittstellen Klasse ^

- Öffentliche Referenzklasse^

- value struct

- Öffentliche Enumerationsklasse

Die Zuordnung ist im Grunde genommen ein Wrapper für [std::map](../standard-library/map-class.md). Dabei handelt es sich um eine konkrete C++-Implementierung der Typen [Windows:: Foundation:: \<Windows::Foundation::Collections::IKeyValuePair\<K,V> > Collections:: IMap](/uwp/api/windows.foundation.collections.imap-2) und [iobservablemap](/uwp/api/windows.foundation.collections.iobservablemap-2) , die über öffentliche Windows-Runtime Schnittstellen übermittelt werden. Wenn Sie versuchen, einen `Platform::Collections::Map` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder des Rückgabewerts in [Windows:: Foundation:: Collections: \<K,V> : IMap](/uwp/api/windows.foundation.collections.imap-2)ändern.

Weitere Informationen finden Sie unter [Collections](../cppcx/collections-c-cx.md).

### <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Map:: map](#ctor)|Initialisiert eine neue Instanz der Map-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Map:: Clear](#clear)|Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.|
|[Map:: First](#first)|Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt.|
|[Map:: GetView](#getview)|Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; das heißt, eine [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map:: Haskey](#haskey)|Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.|
|[Map:: INSERT](#insert)|Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.|
|[Map:: Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen Map-Objekt ab.|
|[Map::Remove](#remove)|Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.|
|[Map:: size](#size)|Gibt die Anzahl von Elementen im aktuellen Map-Objekt zurück.|

### <a name="events"></a>Events

|||
|-|-|
|Name|Beschreibung|
|[Map:: mapchanged](#mapchanged) -Ereignis|Tritt auf, wenn sich die Map ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Map`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a> Map:: Clear-Methode

Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a> Map:: First-Methode

Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt, oder, **`nullptr`** Wenn die Zuordnung leer ist.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Zuordnung angibt.

### <a name="remarks"></a>Hinweise

Eine bequeme Möglichkeit, den von First () zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem **`auto`** typableitungs Schlüsselwort deklariert wird. Beispiel: `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a> Map:: GetView-Methode

Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück. Das heißt, eine [Platform:: Collections:: MapView-Klasse](../cppcx/platform-collections-mapview-class.md), die die Schnittstelle [Windows:: Foundation:: Collections:: imapview \<K,V> ](/uwp/api/windows.foundation.collections.imapview-2) implementiert.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein `MapView`-Objekt.

## <a name="maphaskey-method"></a><a name="haskey"></a> Map:: Haskey-Methode

Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des Map-Elements verwendete Schlüssel. Der *Schlüsseltyp* lautet Typname *K*.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn der Schlüssel gefunden wird. andernfalls **`false`** .

## <a name="mapinsert-method"></a><a name="insert"></a> Map:: Insert-Methode

Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.

### <a name="syntax"></a>Syntax

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* lautet Typname *K*.

*value*<br/>
Der Wertteil des Schlüssel-Wert-Paars. Der *Werttyp* ist Typname *V*.

### <a name="return-value"></a>Rückgabewert

**`true`** Wenn der Schlüssel eines vorhandenen Elements in der aktuellen Zuordnung mit *Key* übereinstimmt und der Wert Teil dieses Elements auf *value*festgelegt ist. **`false`** , wenn kein vorhandenes Element in der aktuellen Zuordnung mit *Key* übereinstimmt und die *Schlüssel* -und *Wert* Parameter in einem Schlüssel-Wert-Paar erstellt und dann der aktuellen Zuordnung hinzugefügt werden.

## <a name="maplookup-method"></a><a name="lookup"></a> Map:: Lookup-Methode

Ruft den Wert des Typs V ab, der mit dem angegebenen Schlüssel des Typs K verknüpft ist, sofern der Schlüssel vorhanden ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der Zuordnung vorhandenen Elements verwendete Schlüssel. Der *Schlüsseltyp* lautet Typname *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der mit dem *Schlüssel*gekoppelt ist. Der Typ des Rückgabewerts ist Typname *V*.

### <a name="remarks"></a>Hinweise

Wenn der Schlüssel nicht vorhanden ist, wird eine [Platform:: outoeboundsexception-Ausnahme](../cppcx/platform-outofboundsexception-class.md) ausgelöst.

## <a name="mapmap-constructor"></a><a name="ctor"></a> Map:: Map-Konstruktor

Initialisiert eine neue Instanz der Map-Klasse.

### <a name="syntax"></a>Syntax

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Parameter

*InIt*<br/>
Der Typname der aktuellen Map.

*comp*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen.

*m*<br/>
Ein Verweis oder ein [Rvalue-Wert](../cpp/lvalues-and-rvalues-visual-cpp.md) für einen `map Class` , der verwendet wird, um die aktuelle Zuordnung zu initialisieren.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a> Map:: mapchanged-Ereignis

Wird ausgelöst, wenn ein Element in eine Zuordnung eingefügt bzw. aus der Zuordnung entfernt wird.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [mapchangedeventhandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) , der Informationen zum Objekt enthält, das das Ereignis ausgelöst hat, sowie die Art der Änderung, die aufgetreten ist. Siehe auch [imapchangedebug \<K> ](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) -und [CollectionChange-Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework

Windows-Runtime apps, die c# oder Visual Basic Project IMap \<K,V> als IDictionary verwenden \<K,V> .

## <a name="mapremove-method"></a><a name="remove"></a> Map:: Remove-Methode

Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* lautet Typname *K*.

## <a name="mapsize-method"></a><a name="size"></a> Map:: size-Methode

Gibt die Anzahl der [Windows:: Foundation:: Collections:: ikeyvaluepair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) -Elemente in der Zuordnung zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der Zuordnung.

## <a name="see-also"></a>Siehe auch

[Auflistungen (C++/CX)](collections-c-cx.md)<br/>
[Platform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
