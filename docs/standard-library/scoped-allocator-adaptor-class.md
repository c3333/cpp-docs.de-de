---
title: scoped_allocator_adaptor-Klasse
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: b08cf1858cb0f9bf4dc6201edc2502d48754ff77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373396"
---
# <a name="scoped_allocator_adaptor-class"></a>scoped_allocator_adaptor-Klasse

Stellt einen Satz von Zuweisern dar.

## <a name="syntax"></a>Syntax

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage kapselt ein Nest mit einem oder mehreren Zuschreibungen. Jede Klasse hat einen äußersten Zuweiser vom Typ `outer_allocator_type`, ein Synonym für `Outer`, das eine öffentliche Basis des `scoped_allocator_adaptor`-Objekts darstellt. Mit `Outer` wird der von einem Container zu verwendende Speicher zugewiesen. Sie erhalten einen Verweis auf dieses Zuweiserbasisobjekt, indem Sie `outer_allocator` aufrufen.

Der Rest des Satzes weist Typ `inner_allocator_type` auf. Mit einem inneren Zuweiser wird Speicher für Elemente in einem Container zugewiesen. Sie erhalten einen Verweis auf das gespeicherte Objekt dieses Typs, indem Sie `inner_allocator` aufrufen. Wenn `Inner...` nicht leer ist, weist `inner_allocator_type` den Typ `scoped_allocator_adaptor<Inner...>` auf, und `inner_allocator` kennzeichnet ein Memberobjekt. Andernfalls weist `inner_allocator_type` den Typ `scoped_allocator_adaptor<Outer>` auf, und `inner_allocator` kennzeichnet das gesamte Objekt.

Der Satz verhält sich so, als hätte er eine beliebige Tiefe, wobei nach Bedarf der innerste gekapselte Zuweiser repliziert wird.

Mehrere Konzepte, die nicht Teil der sichtbaren Schnittstelle sind, helfen bei der Beschreibung des Verhaltens dieser Klassenvorlage. Ein *äußerster Zuweiser* vermittelt alle Aufrufe an die construct- und die destroy-Methode. Er wird durch die rekursive Funktion `OUTERMOST(X)` definiert, wobei `OUTERMOST(X)` eines der folgenden Elemente ist.

- Wenn `X.outer_allocator()` wohlgeformt ist, ist `OUTERMOST(X)` gleich `OUTERMOST(X.outer_allocator())`.

- Andernfalls lautet `OUTERMOST(X)``X`.

Drei Typen werden zum Zwecke der Darstellung generiert:

|type|BESCHREIBUNG|
|----------|-----------------|
|`Outermost`|Der `OUTERMOST(*this)`-Typ.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Erstellt ein `scoped_allocator_adaptor`-Objekt.|

### <a name="typedefs"></a>TypeDefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`const_pointer`|Dieser Typ ist ein Synonym für den `const_pointer`, der dem Zuweiser `Outer` zugeordnet ist.|
|`const_void_pointer`|Dieser Typ ist ein Synonym für den `const_void_pointer`, der dem Zuweiser `Outer` zugeordnet ist.|
|`difference_type`|Dieser Typ ist ein Synonym für den `difference_type`, der dem Zuweiser `Outer` zugeordnet ist.|
|`inner_allocator_type`|Dieser Typ ist ein Synonym für den Typ des geschachtelten Adapters `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Dieser Typ ist ein Synonym für den Typ des Basiszuweisers `Outer`.|
|`pointer`|Dieser Typ ist ein Synonym für den `pointer`, der dem Zuweiser `Outer` zugeordnet ist.|
|`propagate_on_container_copy_assignment`|Der Typ enthält TRUE nur dann, wenn `Outer_traits::propagate_on_container_copy_assignment` oder `inner_allocator_type::propagate_on_container_copy_assignment` TRUE enthalten.|
|`propagate_on_container_move_assignment`|Der Typ enthält TRUE nur dann, wenn `Outer_traits::propagate_on_container_move_assignment` oder `inner_allocator_type::propagate_on_container_move_assignment` TRUE enthalten.|
|`propagate_on_container_swap`|Der Typ enthält TRUE nur dann, wenn `Outer_traits::propagate_on_container_swap` oder `inner_allocator_type::propagate_on_container_swap` TRUE enthalten.|
|`size_type`|Dieser Typ ist ein Synonym für den `size_type`, der dem Zuweiser `Outer` zugeordnet ist.|
|`value_type`|Dieser Typ ist ein Synonym für den `value_type`, der dem Zuweiser `Outer` zugeordnet ist.|
|`void_pointer`|Dieser Typ ist ein Synonym für den `void_pointer`, der dem Zuweiser `Outer` zugeordnet ist.|

### <a name="structs"></a>Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[scoped_allocator_adaptor::Struct neu binden](#rebind_struct)|Definiert den Typ `Outer::rebind\<Other>::other` als Synonym für `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Zuordnen](#allocate)|Weist Speicher mithilfe des `Outer`-Zuweisers zu|
|[Erstellen](#construct)|Erstellt ein Objekt|
|[Freigeben](#deallocate)|Hebt die Zuweisung von Objekten mithilfe des äußeren Zuweisers auf|
|[Zerstören](#destroy)|Zerstört ein angegebenes Objekt|
|[inner_allocator](#inner_allocator)|Ruft einen Verweis auf das gespeicherte Objekt vom Typ `inner_allocator_type` ab|
|[Max_size](#max_size)|Bestimmt die maximale Anzahl von Objekten, die vom äußeren Zuweiser zugewiesen werden kann.|
|[outer_allocator](#outer_allocator)|Ruft einen Verweis auf das gespeicherte Objekt vom Typ `outer_allocator_type` ab|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Erstellt ein neues `scoped_allocator_adaptor`-Objekt mit jedem gespeicherten Zuweiserobjekt, das durch Aufrufen von `select_on_container_copy_construction` für jeden entsprechenden Zuweiser initialisiert wird.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator=](#op_as)||
|[Betreiber== Einzelnachweise ==](#op_eq_eq)||
|[Operator!=](#op_noeq)||

## <a name="requirements"></a>Anforderungen

**Header:** \<scoped_allocator>

**Namespace:** std

## <a name="scoped_allocator_adaptorallocate"></a><a name="allocate"></a>scoped_allocator_adaptor::zuweisen

Weist Speicher mithilfe des `Outer`-Zuweisers zu

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parameter

*Count*\
Die Anzahl von Elementen, für die ausreichend Speicher zugewiesen werden soll.

*Hinweis*\
Ein Zeiger, der möglicherweise das Zuweiserobjekt unterstützt, indem er die Adresse eines Objekts sucht, das vor der Anforderung zugewiesen wurde.

### <a name="return-value"></a>Rückgabewert

Die erste Memberfunktion gibt `Outer_traits::allocate(outer_allocator(), count)` zurück. Die zweite Memberfunktion gibt `Outer_traits::allocate(outer_allocator(), count, hint)` zurück.

## <a name="scoped_allocator_adaptorconstruct"></a><a name="construct"></a>scoped_allocator_adaptor::konstrukt

Erstellt ein Objekt

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Parameter

*Ptr*\
Zeiger auf den Speicherort, in dem das Objekt erstellt werden soll.

*Args*\
Liste von Argumenten

*Ersten*\
Objekt des ersten Typs in einem Paar

*Zweite*\
Objekt des zweiten Typs in einem Paar

*Richting*\
Zu verschiebendes oder kopierendes vorhandenes Objekt

### <a name="remarks"></a>Bemerkungen

Die erste Methode erstellt das Objekt `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`bei `xargs...` *ptr,* indem sie aufruft, wobei eine der folgenden Methoden aufgerufen wird.

- Wenn `uses_allocator<Ty, inner_allocator_type>` FALSE enthält, dann ist `xargs...` gleich `args...`.

- Wenn `uses_allocator<Ty, inner_allocator_type>` und `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` TRUE enthalten, ist `xargs...` gleich `allocator_arg, inner_allocator(), args...`.

- Wenn `uses_allocator<Ty, inner_allocator_type>` und `is_constructible<Ty, args..., inner_allocator()>` TRUE enthalten, ist `xargs...` gleich `args..., inner_allocator()`.

Die zweite Methode erstellt das paar Objekt `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`bei `xargs...` `first...` *ptr,* indem aufgerufen wird, `xargs...` `second...` wobei , wo sie wie in der obigen Liste geändert wird, und `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, wo sie wie in der obigen Liste geändert wird.

Die dritte Methode verhält sich wie `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Die vierte Methode verhält sich wie `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Die fünfte Methode verhält sich wie `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Die sechste Methode verhält sich wie `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="scoped_allocator_adaptordeallocate"></a><a name="deallocate"></a>scoped_allocator_adaptor::deallocate

Hebt die Zuweisung von Objekten mithilfe des äußeren Zuweisers auf

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parameter

*Ptr*\
Ein Zeiger auf den Anfangsort der freizugebenden Objekte.

*Count*\
Die Anzahl der freizugebenden Objekte.

## <a name="scoped_allocator_adaptordestroy"></a><a name="destroy"></a>scoped_allocator_adaptor::destroy

Zerstört ein angegebenes Objekt

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parameter

*Ptr*\
Ein Zeiger auf das Objekt, das zerstört werden soll.

### <a name="return-value"></a>Rückgabewert

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="scoped_allocator_adaptorinner_allocator"></a><a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Ruft einen Verweis auf das gespeicherte Objekt vom Typ `inner_allocator_type` ab

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das gespeicherte Objekt vom Typ `inner_allocator_type`

## <a name="scoped_allocator_adaptormax_size"></a><a name="max_size"></a>scoped_allocator_adaptor::max_size

Bestimmt die maximale Anzahl von Objekten, die vom äußeren Zuweiser zugewiesen werden kann.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Rückgabewert

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as">scoped_allocator_adaptor::operator=

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor::Operator==

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor::Operator!=

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="scoped_allocator_adaptorouter_allocator"></a><a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Ruft einen Verweis auf das gespeicherte Objekt vom Typ `outer_allocator_type` ab

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf das gespeicherte Objekt vom Typ `outer_allocator_type`

## <a name="scoped_allocator_adaptorrebind-struct"></a><a name="rebind_struct"></a>scoped_allocator_adaptor::Struct neu binden

Definiert den Typ `Outer::rebind\<Other>::other` als Synonym für `scoped_allocator_adaptor\<Other, Inner...>`.

struct rebind- typedef Other_traits::rebind\<Andere>\<Other_alloc; typedef scoped_allocator_adaptor Other_alloc, Inner...> andere;

## <a name="scoped_allocator_adaptorscoped_allocator_adaptor-constructor"></a><a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor::scoped_allocator_adaptor Konstrukteur

Erstellt ein `scoped_allocator_adaptor`-Objekt. Enthält auch einen Destruktor.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>Parameter

*Richting*\
Ein vorhandener `scoped_allocator_adaptor`.

*Al*\
Eine vorhandener Zuweiser, der als äußerer Zuweiser verwendet werden soll.

*Ruhepause*\
Eine Liste von Zuweisern, die als innere Zuweiser verwendet werden sollen.

### <a name="remarks"></a>Bemerkungen

Der erste Konstruktorstandard erstellt seine gespeicherten Zuweiserobjekte. Jeder der nächsten drei Konstruktoren erstellt seine gespeicherten Zuweisungsobjekte aus den entsprechenden Objekten *rechts*. Der letzte Konstruktor erstellt seine gespeicherten Zuweiserobjekte aus den entsprechenden Argumenten in der Argumentliste.

## <a name="scoped_allocator_adaptorselect_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Erstellt ein neues `scoped_allocator_adaptor`-Objekt mit jedem gespeicherten Zuweiserobjekt, das durch Aufrufen von `select_on_container_copy_construction` für jeden entsprechenden Zuweiser initialisiert wird.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Rückgabewert

Diese Methode gibt `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())` zurück. Das Ergebnis ist `scoped_allocator_adaptor` ein neues Objekt, bei dem jedes `al.select_on_container_copy_construction()` gespeicherte Zuweisungsobjekt durch Aufrufen des entsprechenden Allokators *al*initialisiert wird.

## <a name="see-also"></a>Siehe auch

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
