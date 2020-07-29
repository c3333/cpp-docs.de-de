---
title: concurrent_priority_queue-Klasse
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 024bd2a100b8a0b871d98a5e6001858b55977565
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230362"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue-Klasse

Die `concurrent_priority_queue`-Klasse ist ein Container, der es mehreren Threads gleichzeitig ermöglicht, für Elemente die Vorgänge "push" und "pop" auszuführen. Elemente werden in Reihenfolge ihrer Priorität per pop ausgelesen, wenn die Priorität mit einem als Vorlagenargument angegebenen Funktionselement bestimmt wird.

## <a name="syntax"></a>Syntax

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Datentyp der Elemente, die in der Prioritäts Warteschlange gespeichert werden sollen.

*_Compare*<br/>
Der Typ des Funktions Objekts, das zwei Element Werte als Sortierschlüssel vergleichen kann, um ihre relative Reihenfolge in der Prioritäts Warteschlange zu bestimmen. Dieses Argument ist optional, und das binäre Prädikat `less<T>` ist der Standardwert.

*_Ax*<br/>
Der Typ, der das gespeicherte Zuweisungs Objekt darstellt, das Details zur Zuordnung und Freigabe von Arbeitsspeicher für die Warteschlange für die gleichzeitige Priorität kapselt. Dieses Argument ist optional, und der Standardwert ist `allocator<T>`.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|`allocator_type`|Ein Typ, der die zuordnerklasse für die Warteschlange für die gleichzeitige Priorität darstellt.|
|`const_reference`|Ein Typ, der einen konstanten Verweis auf ein Element des Typs darstellt, der in einer Warteschlange für gleichzeitige Priorität gespeichert ist.|
|`reference`|Ein Typ, der einen Verweis auf ein Element des Typs darstellt, der in einer Warteschlange für gleichzeitige Priorität gespeichert ist.|
|`size_type`|Ein Typ, der die Anzahl von Elementen in einer Warteschlange mit gleichzeitiger Priorität zählt.|
|`value_type`|Ein Typ, der den in einer Warteschlange für gleichzeitige Priorität gespeicherten Datentyp darstellt.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Ist überladen. Erstellt eine Warteschlange für gleichzeitige Priorität.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Löschen](#clear)|Löscht alle Elemente mit der gleichzeitigen Priorität. Diese Methode ist nicht nebenläufigkeitssicher.|
|[empty](#empty)|Testet, ob die Warteschlange für die gleichzeitige Priorität zum Zeitpunkt des Aufrufs dieser Methode leer ist. Diese Methode ist nebenläufigkeitssicher.|
|[get_allocator](#get_allocator)|Gibt eine Kopie der Zuweisung zurück, die zum Erstellen der Warteschlange für die gleichzeitige Priorität verwendet wurde. Diese Methode ist nebenläufigkeitssicher.|
|[push](#push)|Ist überladen. Fügt der Warteschlange für gleichzeitige Priorität ein Element hinzu. Diese Methode ist nebenläufigkeitssicher.|
|[size](#size)|Gibt die Anzahl der Elemente in der Warteschlange für die gleichzeitige Priorität zurück. Diese Methode ist nebenläufigkeitssicher.|
|[swap](#swap)|Vertauscht den Inhalt von zwei Warteschlangen mit gleichzeitiger Priorität. Diese Methode ist nicht nebenläufigkeitssicher.|
|[try_pop](#try_pop)|Entfernt das Element mit der höchsten Priorität aus der Warteschlange, wenn die Warteschlange nicht leer ist, und gibt es zurück. Diese Methode ist nebenläufigkeitssicher.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator =](#operator_eq)|Ist überladen. Weist den Inhalt eines anderen `concurrent_priority_queue`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.|

## <a name="remarks"></a>Bemerkungen

Ausführliche Informationen zur `concurrent_priority_queue` -Klasse finden Sie unter [parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`concurrent_priority_queue`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** concurrent_priority_queue. h

**Namespace:** Parallelität

## <a name="clear"></a><a name="clear"></a>Klartext

Löscht alle Elemente mit der gleichzeitigen Priorität. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void clear();
```

### <a name="remarks"></a>Bemerkungen

`clear`ist nicht Parallelitäts sicher. Sie müssen sicherstellen, dass keine anderen Threads Methoden in der Warteschlange für gleichzeitige Priorität aufrufen, wenn Sie diese Methode aufrufen. `clear`gibt keinen Arbeitsspeicher frei.

## <a name="concurrent_priority_queue"></a><a name="ctor"></a>concurrent_priority_queue

Erstellt eine Warteschlange für gleichzeitige Priorität.

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>Parameter

*_InputIterator*<br/>
Der Typ des Eingabeiterators.

*_Al*<br/>
Die mit diesem Objekt zu verwendende Zuweisungsklasse.

*_Init_capacity*<br/>
Die Anfangskapazität des `concurrent_priority_queue`-Objekts.

*_Begin*<br/>
Die Position des ersten Elements in dem zu kopierenden Elementbereich.

*_End*<br/>
Die Position des ersten Elements nach dem zu kopierenden Elementbereich.

*_Src*<br/>
Das `concurrent_priority_queue`-Quellobjekt, aus dem Elemente kopiert oder verschoben werden sollen.

### <a name="remarks"></a>Bemerkungen

Alle Konstruktoren speichern ein zuordnerobjekt `_Al` und initialisieren die Prioritäts Warteschlange.

Der erste Konstruktor gibt eine leere Warteschlange für die anfängliche Priorität an und gibt optional eine Zuweisung an.

Der zweite Konstruktor gibt eine Prioritäts Warteschlange mit einer Anfangskapazität an `_Init_capacity` und gibt optional eine Zuweisung an.

Der dritte Konstruktor gibt Werte an, die vom iteratorbereich [,) bereitgestellt werden `_Begin` , `_End` und gibt optional eine Zuweisung an.

Der vierte und fünfte Konstruktor geben eine Kopie der Prioritäts Warteschlange an `_Src` .

Der sechste und der siebte Konstruktor geben eine Verschiebung der Prioritäts Warteschlange an `_Src` .

## <a name="empty"></a><a name="empty"></a>leer

Testet, ob die Warteschlange für die gleichzeitige Priorität zum Zeitpunkt des Aufrufs dieser Methode leer ist. Diese Methode ist nebenläufigkeitssicher.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Prioritäts Warteschlange zum Zeitpunkt des Aufrufs der Funktion leer war, **`false`** andernfalls.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Gibt eine Kopie der Zuweisung zurück, die zum Erstellen der Warteschlange für die gleichzeitige Priorität verwendet wurde. Diese Methode ist nebenläufigkeitssicher.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Kopie der Zuweisung, die zum Erstellen des- `concurrent_priority_queue` Objekts verwendet wird.

## <a name="operator"></a><a name="operator_eq"></a>Operator =

Weist den Inhalt eines anderen `concurrent_priority_queue`-Objekts diesem Objekt zu. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parameter

*_Src*<br/>
Das `concurrent_priority_queue`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das `concurrent_priority_queue`-Objekt.

## <a name="push"></a><a name="push"></a>Push

Fügt der Warteschlange für gleichzeitige Priorität ein Element hinzu. Diese Methode ist nebenläufigkeitssicher.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parameter

*_Elem*<br/>
Das Element, das der Warteschlange für gleichzeitige Priorität hinzugefügt werden soll.

## <a name="size"></a><a name="size"></a>Größe

Gibt die Anzahl der Elemente in der Warteschlange für die gleichzeitige Priorität zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente in diesem- `concurrent_priority_queue` Objekt.

### <a name="remarks"></a>Bemerkungen

Die zurückgegebene Größe schließt garantiert alle Elemente ein, die durch Aufrufe der-Funktion hinzugefügt werden `push` . Die Ergebnisse von ausstehenden gleichzeitigen Vorgängen werden jedoch möglicherweise nicht angezeigt.

## <a name="swap"></a><a name="swap"></a>Wechsel

Vertauscht den Inhalt von zwei Warteschlangen mit gleichzeitiger Priorität. Diese Methode ist nicht nebenläufigkeitssicher.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parameter

*_Queue*<br/>
Das `concurrent_priority_queue`-Objekt, mit dem der Inhalt getauscht werden soll.

## <a name="try_pop"></a><a name="try_pop"></a>try_pop

Entfernt das Element mit der höchsten Priorität aus der Warteschlange, wenn die Warteschlange nicht leer ist, und gibt es zurück. Diese Methode ist nebenläufigkeitssicher.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parameter

*_Elem*<br/>
Ein Verweis auf eine Variable, die mit dem Element mit der höchsten Priorität aufgefüllt wird, wenn die Warteschlange nicht leer ist.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn ein Wert per Pop ausgeblendet wurde, **`false`** andernfalls.

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace](concurrency-namespace.md)<br/>
[Parallele Container und Objekte](../../../parallel/concrt/parallel-containers-and-objects.md)
