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
ms.openlocfilehash: ff27f6c543a2326dd4318f66aae51b89092b28e2
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032446"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map-Klasse

Stellt eine *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist. Implementiert [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) zur Hilfe bei der XAML-Datenbindung . [data binding](/windows/uwp/data-binding/data-binding-in-depth)

## <a name="syntax"></a>Syntax

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parameter

*K*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*V*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen. Standardmäßig [ist\<std::less K>](../standard-library/less-struct.md).

*__is_valid_winrt_type()* Eine vom Compiler generierte Funktion, die den Typ *Von K* und *V* überprüft und eine Anzeigefehlermeldung bereitstellt, wenn der Typ nicht in der Karte gespeichert werden kann.

### <a name="remarks"></a>Bemerkungen

Folgende Typen sind zulässig:

- Ganze Zahlen

- Schnittstellenklasse

- Öffentliche Referenzklasse^

- value struct

- Öffentliche Enumerationsklasse

Die Zuordnung ist im Grunde genommen ein Wrapper für [std::map](../standard-library/map-class.md). Es handelt sich um eine c++-konkrete Implementierung der [Windows::Foundation::Collections::IMap<Windows::Foundation::Collections::IKeyValuePair\<K,V>>](/uwp/api/windows.foundation.collections.imap-2) und [IObservableMap-Typen,](/uwp/api/windows.foundation.collections.iobservablemap-2) die über öffentliche Windows-Runtime-Schnittstellen übergeben werden. Wenn Sie versuchen, einen `Platform::Collections::Map` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, indem Sie den Typ des Parameters oder den Rückgabewert in [Windows::Foundation::Collections::IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2)ändern.

Weitere Informationen finden Sie unter [Sammlungen](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Karte::Karte](#ctor)|Initialisiert eine neue Instanz der Map-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Karte::Clear](#clear)|Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.|
|[Karte::Erste](#first)|Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt.|
|[Karte::GetView](#getview)|Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; das heißt, eine [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Karte::HasKey](#haskey)|Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.|
|[Karte::Einfügen](#insert)|Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.|
|[Karte::Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen Map-Objekt ab.|
|[Map::Remove](#remove)|Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.|
|[Karte::Größe](#size)|Gibt die Anzahl von Elementen im aktuellen Map-Objekt zurück.|

### <a name="events"></a>Ereignisse

|||
|-|-|
|Name|BESCHREIBUNG|
|[Karte::MapChanged-Ereignis](#mapchanged)|Tritt auf, wenn sich die Map ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Map`

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>Karte::Clear-Methode

Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Karte::Erste Methode

Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt, oder `nullptr`, wenn die Zuordnung leer ist.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Zuordnung angibt.

### <a name="remarks"></a>Bemerkungen

Eine bequeme Möglichkeit, den von First() zurückgegebenen Iterator zu halten, besteht darin, den Rückgabewert einer Variablen zuzuweisen, die mit dem Schlüsselwort **"Auto** type deduction" deklariert wird. Beispiel: `auto x = myMap->First();`.

## <a name="mapgetview-method"></a><a name="getview"></a>Karte::GetView-Methode

Gibt eine schreibgeschützte Ansicht der aktuellen Karte zurück. Das heißt, eine [Platform::Collections::MapView-Klasse](../cppcx/platform-collections-mapview-class.md), die die [Windows::Foundation::Collections::IMapView\<K,V->-Schnittstelle](/uwp/api/windows.foundation.collections.imapview-2) implementiert.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein `MapView` -Objekt.

## <a name="maphaskey-method"></a><a name="haskey"></a>Karte::HasKey-Methode

Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des Map-Elements verwendete Schlüssel. Der *Schlüsseltyp* ist der TypName *K*.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Schlüssel gefunden wird; andernfalls **false**.

## <a name="mapinsert-method"></a><a name="insert"></a>Karte::Insert-Methode

Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.

### <a name="syntax"></a>Syntax

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* ist der TypName *K*.

*value*<br/>
Der Wertteil des Schlüssel-Wert-Paars. Der *Werttyp* ist typname *V*.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Schlüssel eines vorhandenen Elements in der aktuellen Karte mit dem *Schlüssel* übereinstimmt und der Wertteil dieses Elements auf *Wert*festgelegt ist. **false,** wenn kein vorhandenes Element in der aktuellen Karte mit dem *Schlüssel* übereinstimmt und die *Schlüssel-* und *Wertparameter* zu einem Schlüssel-Wert-Paar gemacht und dann der aktuellen Karte hinzugefügt werden.

## <a name="maplookup-method"></a><a name="lookup"></a>Karte::Lookup-Methode

Ruft den Wert des Typs V ab, der mit dem angegebenen Schlüssel des Typs K verknüpft ist, sofern der Schlüssel vorhanden ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der Zuordnung vorhandenen Elements verwendete Schlüssel. Der *Schlüsseltyp* ist der TypName *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der mit dem *Schlüssel*gekoppelt ist. Der Typ des Rückgabewerts ist der Typname *V*.

### <a name="remarks"></a>Bemerkungen

Wenn der Schlüssel nicht vorhanden ist, wird eine [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) ausgelöst.

## <a name="mapmap-constructor"></a><a name="ctor"></a>Karte::Map-Konstruktor

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

*Init*<br/>
Der Typname der aktuellen Map.

*Comp*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen.

*M*<br/>
Ein Verweis oder [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) auf eine, `map Class` die zum Initialisieren der aktuellen Karte verwendet wird.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Karte::MapChanged-Ereignis

Wird ausgelöst, wenn ein Element in eine Zuordnung eingefügt bzw. aus der Zuordnung entfernt wird.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [MapChangedEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) der Informationen über das Objekt enthält, das das Ereignis ausgelöst hat, und die Art der Änderungen, die aufgetreten sind. Siehe auch [IMapChangedEventArgs\<K>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1) und [CollectionChange Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework

Windows-Runtime-Apps, die das IMap\<K,V-Projekt\<von C- oder Visual Basic-Projekt verwenden,> als IDictionary K,V>.

## <a name="mapremove-method"></a><a name="remove"></a>Karte::Entfernungsmethode

Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der *Schlüsseltyp* ist der TypName *K*.

## <a name="mapsize-method"></a><a name="size"></a>Karte::Size-Methode

Gibt die Anzahl von [Windows::Foundation::Collections::IKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2) Elementen in der Karte zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der Zuordnung.

## <a name="see-also"></a>Weitere Informationen

[Sammlungen (C++/CX)](collections-c-cx.md)<br/>
[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
