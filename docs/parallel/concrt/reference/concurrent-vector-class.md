---
title: concurrent_vector-Klasse
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 002f1e3f691de3315810efed8f7d8f6c547cf653
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854163"
---
# <a name="concurrent_vector-class"></a>concurrent_vector-Klasse

Die `concurrent_vector`-Klasse ist eine Sequenzcontainerklasse, die zufälligen Zugriff auf jedes Element zulässt. Sie aktiviert parallelitätssichere Operationen für Anfügen, Elementzugriff, Iteratorzugriff und Iteratordurchlauf. Die Parallelitäts Sicherheit bedeutet, dass Zeiger oder Iteratoren immer gültig sind. Es handelt sich nicht um eine Garantie der Element Initialisierung oder einer bestimmten Durchlauf Reihenfolge.

## <a name="syntax"></a>Syntax

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die im Vektor gespeichert werden sollen.

*_Ax*<br/>
Der Typ, der das gespeicherte Zuweisungsobjekt darstellt, das Details zur Speicherbelegung und Aufhebung der Speicherbelegung für den gleichzeitigen Vektor kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<T>`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`allocator_type`|Ein Typ, der die zuordnerklasse für den gleichzeitigen Vektor darstellt.|
|`const_iterator`|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem ein `const` Element in einem gleichzeitigen Vektor gelesen werden kann.|
|`const_pointer`|Ein Typ, der einen Zeiger auf ein `const` Element in einem gleichzeitigen Vektor bereitstellt.|
|`const_reference`|Ein Typ, der einen Verweis auf ein `const` Element bereitstellt, das in einem gleichzeitigen Vektor zum Lesen und Ausführen von `const` Vorgängen gespeichert ist.|
|`const_reverse_iterator`|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes `const` Element im gleichzeitigen Vektor gelesen werden kann.|
|`difference_type`|Ein Typ, der den Abstand mit Vorzeichen zwischen zwei Elementen in einem gleichzeitigen Vektor bereitstellt.|
|`iterator`|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes Element in einem gleichzeitigen Vektor gelesen werden kann. Die Änderung eines Elements, das den Iterator verwendet, ist nicht Parallelitäts sicher.|
|`pointer`|Ein Typ, der einen Zeiger auf ein Element in einem gleichzeitigen Vektor bereitstellt.|
|`reference`|Ein Typ, der einen Verweis auf ein in einem gleichzeitigen Vektor gespeichertes Element bereitstellt.|
|`reverse_iterator`|Ein Typ, der einen Iterator mit zufälligem Zugriff bereitstellt, mit dem jedes Element in einem umgekehrten gleichzeitigen Vektor gelesen werden kann. Die Änderung eines Elements, das den Iterator verwendet, ist nicht Parallelitäts sicher.|
|`size_type`|Ein Typ, der die Anzahl von Elementen in einem gleichzeitigen Vektor zählt.|
|`value_type`|Ein Typ, der den in einem gleichzeitigen Vektor gespeicherten Datentyp darstellt.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[concurrent_vector](#ctor)|Ist überladen. Erstellt einen gleichzeitigen Vektor.|
|[~ concurrent_vector-Dekonstruktor](#dtor)|Löscht alle-Elemente und zerstört diesen gleichzeitigen Vektor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[assign](#assign)|Ist überladen. Löscht die Elemente des gleichzeitigen Vektors und weist diese entweder `_N` Kopien `_Item`oder die durch den iteratorbereich (`_Begin`, `_End`) angegebenen Werte zu. Diese Methode ist nicht nebenläufigkeitssicher.|
|[at](#at)|Ist überladen. Ermöglicht den Zugriff auf das Element am angegebenen Index im gleichzeitigen Vektor. Diese Methode ist für Lesevorgänge Parallelitäts sicher und auch beim Vergrößern des Vektors, solange Sie sichergestellt haben, dass der Wert `_Index` kleiner ist als die Größe des gleichzeitigen Vektors.|
|[Rückseite](#back)|Ist überladen. Gibt einen Verweis oder einen `const` Verweis auf das letzte Element im gleichzeitigen Vektor zurück. Wenn der gleichzeitige Vektor leer ist, ist der Rückgabewert nicht definiert. Diese Methode ist nebenläufigkeitssicher.|
|[begin](#begin)|Ist überladen. Gibt einen Iterator vom Typ `iterator` oder `const_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[Kapazität](#capacity)|Gibt die maximale Größe zurück, mit der der gleichzeitige Vektor vergrößert werden kann, ohne mehr Arbeitsspeicher zuweisen zu müssen. Diese Methode ist nebenläufigkeitssicher.|
|[cbegin](#cbegin)|Gibt einen Iterator vom Typ `const_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[cend](#cend)|Gibt einen Iterator vom Typ `const_iterator` am Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[Löschen](#clear)|Löscht alle Elemente im gleichzeitigen Vektor. Diese Methode ist nicht nebenläufigkeitssicher.|
|[crbegin](#crbegin)|Gibt einen Iterator vom Typ `const_reverse_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[crend](#crend)|Gibt einen Iterator vom Typ `const_reverse_iterator` am Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[empty](#empty)|Testet, ob der gleichzeitige Vektor zum Zeitpunkt des Aufrufs dieser Methode leer ist. Diese Methode ist nebenläufigkeitssicher.|
|[end](#end)|Ist überladen. Gibt einen Iterator vom Typ `iterator` oder `const_iterator` bis zum Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[Vorderseite](#front)|Ist überladen. Gibt einen Verweis oder einen `const` Verweis auf das erste Element im gleichzeitigen Vektor zurück. Wenn der gleichzeitige Vektor leer ist, ist der Rückgabewert nicht definiert. Diese Methode ist nebenläufigkeitssicher.|
|[get_allocator](#get_allocator)|Gibt eine Kopie der Zuweisung zurück, die verwendet wird, um den gleichzeitigen Vektor zu erstellen. Diese Methode ist nebenläufigkeitssicher.|
|[grow_by](#grow_by)|Ist überladen. Vergrößert diesen gleichzeitigen Vektor durch `_Delta`-Elemente. Diese Methode ist nebenläufigkeitssicher.|
|[grow_to_at_least](#grow_to_at_least)|Vergrößert diesen gleichzeitigen Vektor, bis er mindestens `_N` Elemente aufweist. Diese Methode ist nebenläufigkeitssicher.|
|[max_size](#max_size)|Gibt die maximale Anzahl von Elementen zurück, die der gleichzeitige Vektor enthalten kann. Diese Methode ist nebenläufigkeitssicher.|
|[push_back](#push_back)|Ist überladen. Fügt das angegebene Element an das Ende des gleichzeitigen Vektors an. Diese Methode ist nebenläufigkeitssicher.|
|[rbegin](#rbegin)|Ist überladen. Gibt einen Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[rend](#rend)|Ist überladen. Gibt einen Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` bis zum Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.|
|[reserve](#reserve)|Ordnet ausreichend Speicherplatz zu, um den gleichzeitigen Vektor um die Größe `_N` zu vergrößern, ohne später mehr Speicher zuweisen zu müssen. Diese Methode ist nicht nebenläufigkeitssicher.|
|[resize](#resize)|Ist überladen. Ändert die Größe des gleichzeitigen Vektors in die angeforderte Größe, wobei Elemente nach Bedarf gelöscht oder hinzugefügt werden. Diese Methode ist nicht nebenläufigkeitssicher.|
|[shrink_to_fit](#shrink_to_fit)|Komprimiert die interne Darstellung des gleichzeitigen Vektors, um die Fragmentierung zu reduzieren und die Speicherauslastung zu optimieren. Diese Methode ist nicht nebenläufigkeitssicher.|
|[size](#size)|Gibt die Anzahl der Elemente im gleichzeitigen Vektor zurück. Diese Methode ist nebenläufigkeitssicher.|
|[swap](#swap)|Vertauscht den Inhalt von zwei gleichzeitigen Vektoren. Diese Methode ist nicht nebenläufigkeitssicher.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[operator\[\]](#operator_at)|Ist überladen. Ermöglicht den Zugriff auf das Element am angegebenen Index im gleichzeitigen Vektor. Diese Methode ist für Lesevorgänge Parallelitäts sicher und auch beim Anwachsen des Vektors, solange Sie sichergestellt haben, dass der Wert `_Index` kleiner ist als der gleichzeitige Vektor.|
|[operator=](#operator_eq)|Ist überladen. Weist den Inhalt eines anderen `concurrent_vector`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.|

## <a name="remarks"></a>Bemerkungen

Ausführliche Informationen zur `concurrent_vector`-Klasse finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Concurrent_vector. h

**Namespace:** Parallelität

## <a name="assign"></a>einräumen

Löscht die Elemente des gleichzeitigen Vektors und weist diese entweder `_N` Kopien `_Item`oder die durch den iteratorbereich (`_Begin`, `_End`) angegebenen Werte zu. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parameter

*_InputIterator*<br/>
Der Typ des angegebenen Iterators.

*_N*<br/>
Die Anzahl der Elemente, die in den gleichzeitigen Vektor kopiert werden sollen.

*_Item*<br/>
Verweis auf einen Wert, der verwendet wird, um den gleichzeitigen Vektor auszufüllen.

*_Begin*<br/>
Ein Iterator für das erste Element des Quell Bereichs.

*_End*<br/>
Ein Iterator, der hinter dem letzten Element des Quell Bereichs liegt.

### <a name="remarks"></a>Bemerkungen

`assign` ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden für den gleichzeitigen Vektor aufrufen, wenn Sie diese Methode aufrufen.

## <a name="at"></a>an

Ermöglicht den Zugriff auf das Element am angegebenen Index im gleichzeitigen Vektor. Diese Methode ist für Lesevorgänge Parallelitäts sicher und auch beim Vergrößern des Vektors, solange Sie sichergestellt haben, dass der Wert `_Index` kleiner ist als die Größe des gleichzeitigen Vektors.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parameter

*_Index*<br/>
Der Index des abzurufenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element am angegebenen Index.

### <a name="remarks"></a>Bemerkungen

Die Version der Funktions `at`, die einen nicht `const` Verweis zurückgibt, kann nicht verwendet werden, um gleichzeitig aus verschiedenen Threads in das-Element zu schreiben. Ein anderes Synchronisierungs Objekt sollte verwendet werden, um gleichzeitige Lese-und Schreibvorgänge mit demselben Datenelement zu synchronisieren.

Die-Methode löst `out_of_range` aus, wenn `_Index` größer oder gleich der Größe des gleichzeitigen Vektors ist, und `range_error`, wenn der Index für einen unterbrochenen Teil des Vektors steht. Ausführliche Informationen dazu, wie ein Vektor beschädigt werden kann, finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="back"></a>Zurück

Gibt einen Verweis oder einen `const` Verweis auf das letzte Element im gleichzeitigen Vektor zurück. Wenn der gleichzeitige Vektor leer ist, ist der Rückgabewert nicht definiert. Diese Methode ist nebenläufigkeitssicher.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis oder ein `const` Verweis auf das letzte Element im gleichzeitigen Vektor.

## <a name="begin"></a>beginnen

Gibt einen Iterator vom Typ `iterator` oder `const_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `iterator` oder `const_iterator` am Anfang des gleichzeitigen Vektors.

## <a name="capacity"></a>persönlich

Gibt die maximale Größe zurück, mit der der gleichzeitige Vektor vergrößert werden kann, ohne mehr Arbeitsspeicher zuweisen zu müssen. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Größe, auf die der gleichzeitige Vektor vergrößert werden kann, ohne dass mehr Arbeitsspeicher belegt werden muss.

### <a name="remarks"></a>Bemerkungen

Anders als C++ bei einer Standard Bibliothek `vector`werden vorhandene Elemente von einem `concurrent_vector`-Objekt nicht verschoben, wenn mehr Arbeitsspeicher zugewiesen wird.

## <a name="cbegin"></a>cbegin

Gibt einen Iterator vom Typ `const_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `const_iterator` am Anfang des gleichzeitigen Vektors.

## <a name="cend"></a>cend

Gibt einen Iterator vom Typ `const_iterator` am Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `const_iterator` am Ende des gleichzeitigen Vektors.

## <a name="clear"></a>Klartext

Löscht alle Elemente im gleichzeitigen Vektor. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

`clear` ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden für den gleichzeitigen Vektor aufrufen, wenn Sie diese Methode aufrufen. `clear` keine internen Arrays freigibt. Um interne Arrays freizugeben, müssen Sie die Funktion `shrink_to_fit` nach `clear`abrufen.

## <a name="ctor"></a>concurrent_vector

Erstellt einen gleichzeitigen Vektor.

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>Parameter

*M*<br/>
Der allocator-Typ des Quellvektors.

*_InputIterator*<br/>
Der Typ des Eingabeiterators.

*_Al*<br/>
Die mit diesem Objekt zu verwendende Zuweisungsklasse.

*_Vector*<br/>
Das `concurrent_vector`-Quellobjekt, aus dem Elemente kopiert oder verschoben werden sollen.

*_N*<br/>
Die Anfangskapazität des `concurrent_vector`-Objekts.

*_Item*<br/>
Der Wert der Elemente im erstellten Objekt.

*_Begin*<br/>
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*_End*<br/>
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

### <a name="remarks"></a>Bemerkungen

Von allen Konstruktoren wird ein `_Al`-Zuweisungsobjekt gespeichert und der Vektor initialisiert.

Der erste Konstruktor gibt einen leeren anfänglichen Vektor an und gibt den zuordnertyp explizit an. die zu verwendende.

Die zweiten und dritten Konstruktoren geben eine Kopie des parallel ausgeführten `_Vector`-Vektors an.

Der vierte Konstruktor gibt eine Verschiebung des gleichzeitigen `_Vector`-Vektors an.

Der fünfte Konstruktor gibt eine Wiederholung einer angegebenen Anzahl (`_N`) von Elementen des Standardwerts für die Klasse `T`an.

Der sechste Konstruktor gibt eine Wiederholung von (`_N`) Elementen von Wert `_Item`an.

Der letzte Konstruktor gibt die Werte an, die vom iteratorbereich (`_Begin``_End`) bereitgestellt werden.

## <a name="dtor"></a>~ concurrent_vector

Löscht alle-Elemente und zerstört diesen gleichzeitigen Vektor.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a>crbegin

Gibt einen Iterator vom Typ `const_reverse_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `const_reverse_iterator` am Anfang des gleichzeitigen Vektors.

## <a name="crend"></a>crend

Gibt einen Iterator vom Typ `const_reverse_iterator` am Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `const_reverse_iterator` am Ende des gleichzeitigen Vektors.

## <a name="empty"></a>leer

Testet, ob der gleichzeitige Vektor zum Zeitpunkt des Aufrufs dieser Methode leer ist. Diese Methode ist nebenläufigkeitssicher.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**true** , wenn der Vektor zu dem Zeitpunkt, zu dem die Funktion aufgerufen wurde, leer war, andernfalls **false** .

## <a name="end"></a>Schließlich

Gibt einen Iterator vom Typ `iterator` oder `const_iterator` bis zum Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `iterator` oder `const_iterator` am Ende des gleichzeitigen Vektors.

## <a name="front"></a>Beifahrer

Gibt einen Verweis oder einen `const` Verweis auf das erste Element im gleichzeitigen Vektor zurück. Wenn der gleichzeitige Vektor leer ist, ist der Rückgabewert nicht definiert. Diese Methode ist nebenläufigkeitssicher.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis oder ein `const` Verweis auf das erste Element im gleichzeitigen Vektor.

## <a name="get_allocator"></a>get_allocator

Gibt eine Kopie der Zuweisung zurück, die verwendet wird, um den gleichzeitigen Vektor zu erstellen. Diese Methode ist nebenläufigkeitssicher.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Zuweisung, die zum Erstellen des `concurrent_vector` Objekts verwendet wird.

## <a name="grow_by"></a>grow_by

Vergrößert diesen gleichzeitigen Vektor durch `_Delta`-Elemente. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parameter

*_Delta*<br/>
Die Anzahl der Elemente, die an das-Objekt angefügt werden sollen.

*_Item*<br/>
Der Wert, mit dem die neuen Elemente initialisiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Iterator zum ersten angefügten Element.

### <a name="remarks"></a>Bemerkungen

Wenn `_Item` nicht angegeben ist, werden die neuen Elemente standardmäßig erstellt.

## <a name="grow_to_at_least"></a>grow_to_at_least

Vergrößert diesen gleichzeitigen Vektor, bis er mindestens `_N` Elemente aufweist. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parameter

*_N*<br/>
Die neue Mindestgröße für das `concurrent_vector` Objekt.

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der auf den Anfang der angefügten Sequenz zeigt, oder an das Element bei Index `_N`, wenn keine Elemente angehängt wurden.

## <a name="max_size"></a>max_size

Gibt die maximale Anzahl von Elementen zurück, die der gleichzeitige Vektor enthalten kann. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl der Elemente, die das `concurrent_vector` Objekt enthalten kann.

## <a name="operator_eq"></a>Operator =

Weist den Inhalt eines anderen `concurrent_vector`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>Parameter

*M*<br/>
Der allocator-Typ des Quellvektors.

*_Vector*<br/>
Das `concurrent_vector`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `concurrent_vector`-Objekt.

## <a name="operator_at"></a>[]-Operator

Ermöglicht den Zugriff auf das Element am angegebenen Index im gleichzeitigen Vektor. Diese Methode ist für Lesevorgänge Parallelitäts sicher und auch beim Anwachsen des Vektors, solange Sie sichergestellt haben, dass der Wert `_Index` kleiner ist als der gleichzeitige Vektor.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parameter

*_Index*<br/>
Der Index des abzurufenden Elements.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das Element am angegebenen Index.

### <a name="remarks"></a>Bemerkungen

Die Version von `operator []`, die einen nicht `const` Verweis zurückgibt, kann nicht dazu verwendet werden, gleichzeitig aus verschiedenen Threads in das-Element zu schreiben. Ein anderes Synchronisierungs Objekt sollte verwendet werden, um gleichzeitige Lese-und Schreibvorgänge mit demselben Datenelement zu synchronisieren.

Es wird keine Überprüfung der Begrenzungen durchgeführt, um sicherzustellen, dass `_Index` ein gültiger Index im gleichzeitigen Vektor ist.

## <a name="push_back"></a>push_back

Fügt das angegebene Element an das Ende des gleichzeitigen Vektors an. Diese Methode ist nebenläufigkeitssicher.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parameter

*_Item*<br/>
Der anzufügende Wert.

### <a name="return-value"></a>Rückgabewert

Ein Iterator für das angefügte Element.

## <a name="rbegin"></a>rbegin

Gibt einen Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` an den Anfang des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` am Anfang des gleichzeitigen Vektors.

## <a name="rend"></a>rend

Gibt einen Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` bis zum Ende des gleichzeitigen Vektors zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator vom Typ `reverse_iterator` oder `const_reverse_iterator` am Ende des gleichzeitigen Vektors.

## <a name="reserve"></a>Schutz

Ordnet ausreichend Speicherplatz zu, um den gleichzeitigen Vektor um die Größe `_N` zu vergrößern, ohne später mehr Speicher zuweisen zu müssen. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>Parameter

*_N*<br/>
Die Anzahl der Elemente, für die Platz reserviert werden soll.

### <a name="remarks"></a>Bemerkungen

`reserve` ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden für den gleichzeitigen Vektor aufrufen, wenn Sie diese Methode aufrufen. Die Kapazität des gleichzeitigen Vektors nach dem Zurückgeben der Methode ist möglicherweise größer als die angeforderte Reservierung.

## <a name="resize"></a>Größe

Ändert die Größe des gleichzeitigen Vektors in die angeforderte Größe, wobei Elemente nach Bedarf gelöscht oder hinzugefügt werden. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parameter

*_N*<br/>
Die neue Größe des Concurrent_vector.

*val*<br/>
Der Wert der neuen Elemente, die dem Vektor hinzugefügt werden, wenn die neue Größe die ursprüngliche Größe überschreitet. Wenn der Wert ausgelassen wird, werden den neuen-Objekten der Standardwert für Ihren Typ zugewiesen.

### <a name="remarks"></a>Bemerkungen

Wenn die Größe des Containers kleiner als die angeforderte Größe ist, werden dem Vektor-Elemente hinzugefügt, bis die angeforderte Größe erreicht wird. Wenn die Größe des Containers die angeforderte Größe überschreitet, werden die Elemente, die dem Ende des Containers am nächsten sind, gelöscht, bis der Container die Größe `_N`erreicht. Wenn die tatsächliche Größe des Containers der angeforderten Größe entspricht, wird keine Aktion durchgeführt.

`resize` ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden für den gleichzeitigen Vektor aufrufen, wenn Sie diese Methode aufrufen.

## <a name="shrink_to_fit"></a>shrink_to_fit

Komprimiert die interne Darstellung des gleichzeitigen Vektors, um die Fragmentierung zu reduzieren und die Speicherauslastung zu optimieren. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode werden Arbeitsspeicher Verschiebungs Elemente intern neu belegt, sodass alle Iteratoren ungültig werden. `shrink_to_fit` ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden für den gleichzeitigen Vektor aufrufen, wenn Sie diese Funktion aufrufen.

## <a name="size"></a>Größe

Gibt die Anzahl der Elemente im gleichzeitigen Vektor zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in diesem `concurrent_vector` Objekt.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Größe umfasst garantiert alle Elemente, die von Aufrufen an die Funktions `push_back`angefügt werden, oder Anfügevorgänge, die vor dem Aufrufen dieser Methode abgeschlossen wurden. Es kann jedoch auch Elemente enthalten, die zugeordnet sind, aber noch in der Erstellung durch gleichzeitige Aufrufe einer der wachstumsmethoden vorhanden sind.

## <a name="swap"></a>Wechsel

Vertauscht den Inhalt von zwei gleichzeitigen Vektoren. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parameter

*_Vector*<br/>
Das `concurrent_vector`-Objekt, mit dem der Inhalt getauscht werden soll.

## <a name="see-also"></a>Weitere Informationen

[Concurrency-Namespace](concurrency-namespace.md)<br/>
[Parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md)
