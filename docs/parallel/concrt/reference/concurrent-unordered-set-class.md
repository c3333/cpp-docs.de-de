---
title: concurrent_unordered_set-Klasse
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
ms.openlocfilehash: 8dbce21efcd6c1df31d42702aa3e8eeecf6d9114
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194042"
---
# <a name="concurrent_unordered_set-class"></a>concurrent_unordered_set-Klasse

Die `concurrent_unordered_set` -Klasse ist ein Parallelitäts sicherer Container, der eine Sequenz von Elementen vom Typ K variabler Länge steuert. Die Sequenz wird so dargestellt, dass Parallelitäts sicheres anfügen, Element Zugriff, iteratorzugriff und iteratortraversal-Vorgänge ermöglicht wird. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge.

## <a name="syntax"></a>Syntax

```cpp
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    false>>;
```

### <a name="parameters"></a>Parameter

*Km*<br/>
Der Schlüsseltyp.

*_Hasher*<br/>
Der Hashfunktionsobjekttyp. Dieses Argument ist optional, und der Standardwert ist `std::hash<K>`.

*key_equality*<br/>
Der Gleichheitsvergleich-Funktionsobjekttyp. Dieses Argument ist optional, und der Standardwert ist `std::equal_to<K>`.

*_Allocator_type*<br/>
Der Typ, der das gespeicherte Zuordnungsobjekt darstellt, das Details zur Zuordnung und zur Freigabe des Arbeitsspeichers für den gleichzeitigen ungeordneten Satz kapselt. Dieses Argument ist optional, und der Standardwert ist `std::allocator<K>`.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
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
|`pointer`|Der Typ eines Zeigers auf ein Element.|
|`reference`|Der Typ eines Verweises auf ein Element.|
|`size_type`|Der Typ eines Abstands ohne Vorzeichen zwischen zwei Elementen.|
|`value_type`|Der Typ eines Elements.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[concurrent_unordered_set](#ctor)|Ist überladen. Erstellt einen parallelen ungeordneten Satz.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[hash_function](#hash_function)|Gibt das gespeicherte Hashfunktionsobjekt zurück.|
|[insert](#insert)|Ist überladen. Fügt dem `concurrent_unordered_set`-Objekt Elemente hinzu.|
|[key_eq](#key_eq)|Gibt das gespeicherte Gleichheitsvergleich-Funktionsobjekt zurück.|
|[swap](#swap)|Vertauscht den Inhalt von zwei `concurrent_unordered_set`-Objekten. Diese Methode ist nicht nebenläufigkeitssicher.|
|[unsafe_erase](#unsafe_erase)|Ist überladen. Entfernt Elemente aus der `concurrent_unordered_set` an angegebenen Positionen. Diese Methode ist nicht nebenläufigkeitssicher.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Operator =](#operator_eq)|Ist überladen. Weist den Inhalt eines anderen `concurrent_unordered_set`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.|

## <a name="remarks"></a>Bemerkungen

Ausführliche Informationen zur `concurrent_unordered_set` -Klasse finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_set`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concurrent_unordered_set. h

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

## <a name="concurrent_unordered_set"></a><a name="ctor"></a>concurrent_unordered_set

Erstellt einen parallelen ungeordneten Satz.

```cpp
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Parameter

*_Iterator*<br/>
Der Typ des Eingabeiterators.

*_Number_of_buckets*<br/>
Die anfängliche Anzahl von Buchern für diese ungeordnete Menge.

*_Hasher*<br/>
Die Hash Funktion für diese ungeordnete Menge.

*key_equality*<br/>
Die Gleichheits Vergleichsfunktion für diese ungeordnete Menge.

*_Allocator*<br/>
Die Zuweisung für diesen ungeordneten Satz.

*first*<br/>
*last*<br/>
*_Uset*<br/>
Das `concurrent_unordered_set`-Quellobjekt, aus dem Elemente kopiert oder verschoben werden sollen.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein `_Allocator` zuordnerobjekt und initialisieren den ungeordneten Satz.

Der erste Konstruktor gibt eine leere anfängliche Menge an und gibt explizit die Anzahl der zu verwendenden Bucket, Hash Funktion, Gleichheits Funktion und Zuordnungs Typen an.

Der zweite Konstruktor gibt eine Zuweisung für den ungeordneten Satz an.

Der dritte Konstruktor gibt Werte an, die vom iteratorbereich [,) bereitgestellt werden `_Begin` `_End` .

Der vierte und fünfte Konstruktor geben eine Kopie der gleichzeitigen ungeordneten Menge an `_Uset` .

Der letzte Konstruktor gibt eine Verschiebung des gleichzeitigen ungeordneten Satzes an `_Uset` .

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

Fügt dem `concurrent_unordered_set`-Objekt Elemente hinzu.

```cpp
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
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
Der Typ des Werts, der in den Satz eingefügt wurde.

*value*<br/>
Der einzufügende Wert.

*_Where*<br/>
Die Startposition für die Suche nach einer Einfügemarke.

*first*<br/>
Der Anfang des einzufügenden Bereichs.

*last*<br/>
Das Ende des einzufügenden Bereichs.

### <a name="return-value"></a>Rückgabewert

Ein paar, das einen Iterator und einen booleschen Wert enthält. Weitere Details finden Sie im Abschnitt „Anmerkungen“.

### <a name="remarks"></a>Bemerkungen

Die erste Member-Funktion bestimmt, ob ein Element X in der Sequenz vorhanden ist, deren Schlüssel eine entsprechende Reihenfolge aufweist `value` . Wenn dies nicht der Fall ist, wird ein solches Element X erstellt und mit initialisiert `value` . Die-Funktion bestimmt dann den Iterator `where` , der X festlegt. Wenn eine Einfügung aufgetreten ist, gibt die Funktion zurück `std::pair(where, true)` . Andernfalls wird `std::pair(where, false)`zurückgegeben.

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

Weist den Inhalt eines anderen `concurrent_unordered_set`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```

### <a name="parameters"></a>Parameter

*_Uset*<br/>
Das `concurrent_unordered_set`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `concurrent_unordered_set`-Objekt.

### <a name="remarks"></a>Bemerkungen

Nachdem alle vorhandenen Elemente in einem gleichzeitigen ungeordneten Satz gelöscht wurden, `operator=` kopiert oder verschiebt den Inhalt von `_Uset` in den gleichzeitigen ungeordneten Satz.

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

Vertauscht den Inhalt von zwei `concurrent_unordered_set`-Objekten. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void swap(concurrent_unordered_set& _Uset);
```

### <a name="parameters"></a>Parameter

*_Uset*<br/>
Das `concurrent_unordered_set` Objekt, mit dem getauscht werden soll.

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

Entfernt Elemente aus der `concurrent_unordered_set` an angegebenen Positionen. Diese Methode ist nicht nebenläufigkeitssicher.

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

Die ersten beiden Member-Funktionen geben einen Iterator zurück, der das erste über die entfernten Elemente hinaus verbliebene Element festlegt, oder [End](#end)(), wenn kein solches Element vorhanden ist. Die dritte Memberfunktion gibt die Anzahl von Elementen zurück, die sie entfernt.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion entfernt das Element, auf das durch `_Where` gezeigt wird. Die zweite Member-Funktion entfernt die Elemente im Bereich [ `_Begin` , `_End` ).

Die dritte Member-Funktion entfernt die Elemente im Bereich, der durch [equal_range](#equal_range)(kval) begrenzt ist.

## <a name="unsafe_max_bucket_count"></a><a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Gibt die maximale Anzahl von bucketin diesem Container zurück.

```cpp
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Buchern in diesem Container.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md)
