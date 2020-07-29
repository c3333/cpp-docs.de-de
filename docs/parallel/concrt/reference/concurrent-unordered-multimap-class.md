---
title: concurrent_unordered_multimap-Klasse
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::concurrent_unordered_multimap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_multimap::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_multimap class
ms.assetid: 4dada5d7-15df-4382-b9c9-348e75b2f3c1
ms.openlocfilehash: fb03d368b7c9cced8961dbd77f22ab6bec40bc0d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230323"
---
# <a name="concurrent_unordered_multimap-class"></a>concurrent_unordered_multimap-Klasse

Die `concurrent_unordered_multimap`- Klasse ist ein parallelitätssicherer Container, mit dem eine Folge von Elementen variierender Länge des Typs `std::pair<const K, _Element_type>` steuert. Die Sequenz wird so dargestellt, dass parallelitätssichere Vorgänge für Anfügen, Elementzugriff, Iteratorzugriff und Iteratordurchläufe ermöglicht werden. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge.

## <a name="syntax"></a>Syntax

```cpp
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_multimap : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
true>>;
```

### <a name="parameters"></a>Parameter

*Km*<br/>
Der Schlüsseltyp.

*_Element_type*<br/>
Der zugeordnete Typ.

*_Hasher*<br/>
Der Hashfunktionsobjekttyp. Dieses Argument ist optional, und der Standardwert ist `std::hash<K>`.

*key_equality*<br/>
Der Gleichheitsvergleich-Funktionsobjekttyp. Dieses Argument ist optional, und der Standardwert ist `std::equal_to<K>`.

*_Allocator_type*<br/>
Der Typ, der das gespeicherte Zuweisungsobjekt darstellt, das Details zur Speicherbelegung und Aufhebung der Speicherbelegung für den gleichzeitigen Vektor kapselt. Dieses Argument ist optional, und der Standardwert ist `std::allocator<std::pair<K` , `_Element_type>>` .

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|`allocator_type`|Der Typ einer Zuweisung für die Speicherverwaltung.|
|`const_iterator`|Der Typ eines konstanten Iterators für die gesteuerte Sequenz.|
|`const_local_iterator`|Der Typ eines konstanten Bucketiterators für die gesteuerte Sequenz.|
|`const_pointer`|Der Typ eines konstanten Zeigers auf ein Element.|
|`const_reference`|Der Typ eines konstanten Verweises auf ein Element.|
|`difference_type`|Der Typ eines Abstands mit Vorzeichen zwischen zwei Elementen.|
|`hasher`|Der Typ der Hashfunktion.|
|`iterator`|Der Typ eines Iterators für die gesteuerte Sequenz.|
|`key_equal`|Der Typ der Vergleichsfunktion.|
|`key_type`|Der Typ eines Sortierschlüssels.|
|`local_iterator`|Der Typ eines Bucketiterators für die gesteuerte Sequenz.|
|`mapped_type`|Der Typ eines zugeordneten Werts, der jedem Schlüssel zugeordnet ist.|
|`pointer`|Der Typ eines Zeigers auf ein Element.|
|`reference`|Der Typ eines Verweises auf ein Element.|
|`size_type`|Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.|
|`value_type`|Der Typ eines Elements.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[concurrent_unordered_multimap](#ctor)|Ist überladen. Erstellt eine gleichzeitige ungeordnete Multimap.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[hash_function](#hash_function)|Gibt das gespeicherte Hashfunktionsobjekt zurück.|
|[insert](#insert)|Ist überladen. Fügt dem `concurrent_unordered_multimap`-Objekt Elemente hinzu.|
|[key_eq](#key_eq)|Gibt das gespeicherte Gleichheitsvergleich-Funktionsobjekt zurück.|
|[swap](#swap)|Vertauscht den Inhalt von zwei `concurrent_unordered_multimap`-Objekten. Diese Methode ist nicht nebenläufigkeitssicher.|
|[unsafe_erase](#unsafe_erase)|Ist überladen. Entfernt Elemente aus der `concurrent_unordered_multimap` an angegebenen Positionen. Diese Methode ist nicht nebenläufigkeitssicher.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator =](#operator_eq)|Ist überladen. Weist den Inhalt eines anderen `concurrent_unordered_multimap`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.|

## <a name="remarks"></a>Bemerkungen

Ausführliche Informationen zur `concurrent_unordered_multimap` -Klasse finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_multimap`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concurrent_unordered_map. h

**Namespace:** Parallelität

## <a name="begin"></a><a name="begin"></a>beginnen

Gibt einen Iterator zurück, der auf das erste Element im gleichzeitigen Container zeigt. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator für das erste Element im gleichzeitigen Container.

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

Gibt einen const-Iterator zurück, der auf das erste Element im gleichzeitigen Container zeigt. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const-Iterator für das erste Element im gleichzeitigen Container.

## <a name="cend"></a><a name="cend"></a>cend

Gibt einen const-Iterator zurück, der auf den Speicherort verweist, der dem letzten Element im gleichzeitigen Container nachfolgt. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein const-Iterator für den Speicherort, der dem letzten Element im gleichzeitigen Container nachfolgt.

## <a name="clear"></a><a name="clear"></a>Klartext

Löscht alle Elemente im gleichzeitigen Container. Diese Funktion ist nicht Parallelitäts sicher.

```cpp
void clear();
```

## <a name="concurrent_unordered_multimap"></a><a name="ctor"></a>concurrent_unordered_multimap

Erstellt eine gleichzeitige ungeordnete Multimap.

```cpp
explicit concurrent_unordered_multimap(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multimap(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap(
    const concurrent_unordered_multimap& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_multimap(
    concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der Typ des Eingabeiterators.

*_Number_of_buckets*<br/>
Die anfängliche Anzahl von bucketzuordnungen für diese ungeordnete mehrfach Zuordnung.

*_Hasher*<br/>
Die Hash Funktion für diese ungeordnete mehrfach Zuordnung.

*key_equality*<br/>
Die Gleichheits Vergleichsfunktion für diese ungeordnete mehrfach Zuordnung.

*_Allocator*<br/>
Die Zuweisung für diese ungeordnete mehrfach Zuordnung.

*_Begin*<br/>
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*_End*<br/>
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*_Umap*<br/>
Das Quell `concurrent_unordered_multimap` Objekt, aus dem Elemente kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein Zuordnungs Objekt `_Allocator` und initialisieren die ungeordnete mehrfach Zuordnung.

Der erste Konstruktor gibt eine leere anfängliche mehrfach Zuordnung an und gibt explizit die Anzahl der Bucket, die Hash Funktion, die Gleichheits Funktion und den Zuordnungs Typ an, die verwendet werden sollen.

Der zweite Konstruktor gibt eine Zuweisung für die ungeordnete mehrfach Zuordnung an.

Der dritte Konstruktor gibt Werte an, die vom iteratorbereich [,) bereitgestellt werden `_Begin` `_End` .

Der vierte und fünfte Konstruktor geben eine Kopie der gleichzeitigen ungeordneten mehrfach Zuordnung an `_Umap` .

Der letzte Konstruktor gibt eine Verschiebung der gleichzeitigen ungeordneten mehrfach Zuordnung an `_Umap` .

## <a name="count"></a><a name="count"></a>Countdown

Zählt die Anzahl der Elemente, die mit einem angegebenen Schlüssel übereinstimmen. Diese Funktion ist Parallelitäts sicher.

```cpp
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameter

*Kval*<br/>
Der zu suchende Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt an, wie oft der Schlüssel im Container angezeigt wird.

## <a name="empty"></a><a name="empty"></a>leer

Testet, ob keine Elemente vorhanden sind. Diese Methode ist nebenläufigkeitssicher.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der parallele Container leer ist, **`false`** andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn gleichzeitige Einfügungen vorhanden sind, ändert sich der gleichzeitige Container möglicherweise sofort nach dem Aufruf dieser Funktion, bevor der Rückgabewert gerade gelesen wird.

## <a name="end"></a><a name="end"></a>Schließlich

Gibt einen Iterator zurück, der auf den Speicherort verweist, der dem letzten Element im gleichzeitigen Container nachfolgt. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator für den Speicherort, der dem letzten Element im gleichzeitigen Container nachfolgt.

## <a name="equal_range"></a><a name="equal_range"></a>equal_range

Sucht einen Bereich, der einem angegebenen Schlüssel entspricht. Diese Funktion ist Parallelitäts sicher.

```cpp
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parameter

*Kval*<br/>
Der Schlüsselwert, der gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein [paar](../../../standard-library/pair-structure.md) , bei dem das erste Element ein Iterator für den Anfang und das zweite Element ein Iterator bis zum Ende des Bereichs ist.

### <a name="remarks"></a>Bemerkungen

Gleichzeitige Einfügungen können bewirken, dass nach dem BEGIN-Iterator und vor dem End-Iterator zusätzliche Schlüssel eingefügt werden.

## <a name="find"></a><a name="find"></a>sich

Sucht ein Element, das einem angegebenen Schlüssel entspricht. Diese Funktion ist Parallelitäts sicher.

```cpp
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameter

*Kval*<br/>
Der Schlüsselwert, der gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf die Position des ersten Elements verweist, das mit dem angegebenen Schlüssel übereinstimmt, oder der Iterator, `end()` Wenn kein solches Element vorhanden ist.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Gibt das gespeicherte Zuweisungsobjekt für diesen gleichzeitigen Container zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Zuweisungsobjekt für diesen gleichzeitigen Container.

## <a name="hash_function"></a><a name="hash_function"></a>hash_function

Gibt das gespeicherte Hashfunktionsobjekt zurück.

```cpp
hasher hash_function() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Hash Funktions Objekt.

## <a name="insert"></a><a name="insert"></a>setze

Fügt dem `concurrent_unordered_multimap`-Objekt Elemente hinzu.

```cpp
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der zum Einfügen verwendete iteratortyp.

*Ramelow*<br/>
Der Typ des Werts, der in die Zuordnung eingefügt wurde.

*value*<br/>
Der einzufügende Wert.

*_Where*<br/>
Die Startposition für die Suche nach einer Einfügemarke.

*first*<br/>
Der Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf die Einfügeposition zeigt.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion fügt das-Element `value` in die gesteuerte Sequenz ein und gibt dann den Iterator zurück, der das eingefügte-Element festlegt.

Die zweite Member-Funktion gibt Insert ( `value` ) zurück, wobei `_Where` als Ausgangspunkt innerhalb der kontrollierten Sequenz verwendet wird, um nach der Einfügemarke zu suchen.

Die dritte Member-Funktion fügt die Sequenz von Element Werten aus dem Bereich [ `first` , `last` ) ein.

Die letzten zwei Element Funktionen Verhalten sich identisch mit den ersten beiden, außer dass `value` zum Erstellen des eingefügten Werts verwendet wird.

## <a name="key_eq"></a><a name="key_eq"></a>key_eq

Gibt das gespeicherte Gleichheitsvergleich-Funktionsobjekt zurück.

```cpp
key_equal key_eq() const;
```

### <a name="return-value"></a>Rückgabewert

Das gespeicherte Gleichheitsvergleichsfunktionsobjekt.

## <a name="load_factor"></a><a name="load_factor"></a>load_factor

Berechnet den aktuellen Ladefaktor des Containers und gibt diesen zurück. Der Ladefaktor ist die Anzahl der Elemente im Container dividiert durch die Anzahl der Bucket.

```cpp
float load_factor() const;
```

### <a name="return-value"></a>Rückgabewert

Der Ladefaktor für den Container.

## <a name="max_load_factor"></a><a name="max_load_factor"></a>max_load_factor

Ruft den maximalen Ladefaktor des Containers ab oder legt ihn fest. Der maximale Ladefaktor ist die größte Anzahl von Elementen, als in einem Bucket vorhanden sein können, bevor der Container seine interne Tabelle vergrößert.

```cpp
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parameter

`_Newmax`

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt den gespeicherten maximalen Lastfaktor zurück. Die zweite Member-Funktion gibt keinen Wert zurück, löst jedoch eine [Out_of_range](../../../standard-library/out-of-range-class.md) Ausnahme aus, wenn der angegebene Lastfaktor ungültig ist.

## <a name="max_size"></a><a name="max_size"></a>max_size

Gibt die maximale Größe des gleichzeitigen Containers zurück, der durch die Zuweisung bestimmt wird. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Elementen, die in diesen gleichzeitigen Container eingefügt werden können.

### <a name="remarks"></a>Bemerkungen

Dieser obere Grenzwert ist möglicherweise höher als der tatsächliche Container.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Weist den Inhalt eines anderen `concurrent_unordered_multimap`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
concurrent_unordered_multimap& operator= (const concurrent_unordered_multimap& _Umap);

concurrent_unordered_multimap& operator= (concurrent_unordered_multimap&& _Umap);
```

### <a name="parameters"></a>Parameter

*_Umap*<br/>
Das `concurrent_unordered_multimap`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `concurrent_unordered_multimap`-Objekt.

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in einer gleichzeitigen ungeordneten multimap gelöscht wurden, `operator=` kopiert oder verschiebt den Inhalt von `_Umap` in die gleichzeitige ungeordnete multimap.

## <a name="rehash"></a><a name="rehash"></a>rehash

Erstellt die Hashtabelle neu.

```cpp
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parameter

*_Buckets*<br/>
Die gewünschte Anzahl von Buchern.

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion ändert die Anzahl der Buckets in mindestens `_Buckets` und erstellt ggf. die Hashtabelle neu. Die Bucketanzahl muss eine Potenz von 2 sein. Wenn keine Potenz von 2 ist, wird Sie auf die nächste größte Potenz von 2 aufgerundet.

Es wird eine [Out_of_range](../../../standard-library/out-of-range-class.md) Ausnahme ausgelöst, wenn die Anzahl der bucketwerte ungültig ist (entweder 0 oder größer als die maximale Anzahl von Buchern).

## <a name="size"></a><a name="size"></a>Größe

Gibt die Anzahl der Elemente in diesem gleichzeitigen Container zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Container.

### <a name="remarks"></a>Bemerkungen

Wenn gleichzeitige Einfügungen vorhanden sind, kann sich die Anzahl der Elemente im gleichzeitigen Container unmittelbar nach dem Aufruf dieser Funktion ändern, bevor der Rückgabewert gerade gelesen wird.

## <a name="swap"></a><a name="swap"></a>Wechsel

Vertauscht den Inhalt von zwei `concurrent_unordered_multimap`-Objekten. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void swap(concurrent_unordered_multimap& _Umap);
```

### <a name="parameters"></a>Parameter

*_Umap*<br/>
Das `concurrent_unordered_multimap` Objekt, mit dem getauscht werden soll.

## <a name="unsafe_begin"></a><a name="unsafe_begin"></a>unsafe_begin

Gibt einen Iterator zum ersten Element in diesem Container für einen bestimmten Bucket zurück.

```cpp
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameter

*_Bucket*<br/>
Der Bucket-Index.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang des Bucket zeigt.

## <a name="unsafe_bucket"></a><a name="unsafe_bucket"></a>unsafe_bucket

Gibt den Bucket-Index zurück, dem ein bestimmter Schlüssel in diesem Container zugeordnet ist.

```cpp
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parameter

*Kval*<br/>
Der Element Schlüssel, nach dem gesucht wird.

### <a name="return-value"></a>Rückgabewert

Der Bucket-Index für den Schlüssel in diesem Container.

## <a name="unsafe_bucket_count"></a><a name="unsafe_bucket_count"></a>unsafe_bucket_count

Gibt die aktuelle Anzahl der Bucket in diesem Container zurück.

```cpp
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl von Buchern in diesem Container.

## <a name="unsafe_bucket_size"></a><a name="unsafe_bucket_size"></a>unsafe_bucket_size

Gibt die Anzahl der Elemente in einem bestimmten Bucket dieses Containers zurück.

```cpp
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parameter

*_Bucket*<br/>
Der zu suchende Bucket.

### <a name="return-value"></a>Rückgabewert

Die aktuelle Anzahl von Buchern in diesem Container.

## <a name="unsafe_cbegin"></a><a name="unsafe_cbegin"></a>unsafe_cbegin

Gibt einen Iterator zum ersten Element in diesem Container für einen bestimmten Bucket zurück.

```cpp
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameter

*_Bucket*<br/>
Der Bucket-Index.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang des Bucket zeigt.

## <a name="unsafe_cend"></a><a name="unsafe_cend"></a>unsafe_cend

Gibt einen Iterator an den Speicherort zurück, der dem letzten Element in einem bestimmten Bucket nachfolgt.

```cpp
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameter

*_Bucket*<br/>
Der Bucket-Index.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang des Bucket zeigt.

## <a name="unsafe_end"></a><a name="unsafe_end"></a>unsafe_end

Gibt einen Iterator für das letzte Element in diesem Container für einen bestimmten Bucket zurück.

```cpp
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parameter

*_Bucket*<br/>
Der Bucket-Index.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf das Ende des Bucket zeigt.

## <a name="unsafe_erase"></a><a name="unsafe_erase"></a>unsafe_erase

Entfernt Elemente aus der `concurrent_unordered_multimap` an angegebenen Positionen. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameter

*_Where*<br/>
Die Position des Iterators, an der gelöscht werden soll.

*Kval*<br/>
Der Schlüsselwert, der gelöscht werden soll.

*first*<br/>
*last*<br/>
Iteratoren.

### <a name="return-value"></a>Rückgabewert

Die ersten beiden Memberfunktionen geben einen Iterator zurück, der das erste Element festlegt, das länger als alle anderen entfernten Elementen verbleibt, oder er gibt `concurrent_unordered_multimap::end`() zurück, wenn kein solches Element vorhanden ist. Die dritte Memberfunktion gibt die Anzahl von Elementen zurück, die sie entfernt.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion entfernt das-Element der kontrollierten Sequenz, auf die von verwiesen wird `_Where` . Die zweite Member-Funktion entfernt die Elemente im Bereich [ `_Begin` , `_End` ).

Die dritte Member-Funktion entfernt die Elemente im durch `concurrent_unordered_multimap::equal_range` (kval) getrennten Bereich.

## <a name="unsafe_max_bucket_count"></a><a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Gibt die maximale Anzahl von bucketin diesem Container zurück.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Buchern in diesem Container.

## <a name="see-also"></a>Siehe auch

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md)
