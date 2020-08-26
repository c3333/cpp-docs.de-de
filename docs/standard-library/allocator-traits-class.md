---
title: allocator_traits-Klasse
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 8ab46ebf85531af052bc19bc5f0088f0f564793b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844807"
---
# <a name="allocator_traits-class"></a>allocator_traits-Klasse

Die Klassen Vorlage beschreibt ein Objekt, das einen *zuordnertyp*ergänzt. Ein Allocatortyp ist jeder Typ, der ein Zuweisungsobjekt beschreibt, das zum Verwalten von zugewiesenem Speicherplatz verwendet wird. Sie können insbesondere für jeden Allocator des Typs `Alloc``allocator_traits<Alloc>` verwenden, um alle Informationen zu erhalten, die für einen zuweisungsfähigen Container erforderlich sind. Weitere Informationen finden Sie unter der Standard-[Allocator-Klasse](allocator-class.md).

## <a name="syntax"></a>Syntax

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|`allocator_type`|Dieser Typ stellt ein Synonym für den Vorlagenparameter `Alloc`dar.|
|`const_pointer`|Dieser Typ ist `Alloc::const_pointer`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `pointer_traits<pointer>::rebind<const value_type>`.|
|`const_void_pointer`|Dieser Typ ist `Alloc::const_void_pointer`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `pointer_traits<pointer>::rebind<const void>`.|
|`difference_type`|Dieser Typ ist `Alloc::difference_type`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `pointer_traits<pointer>::difference_type`.|
|`pointer`|Dieser Typ ist `Alloc::pointer`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `value_type *`.|
|`propagate_on_container_copy_assignment`|Dieser Typ ist `Alloc::propagate_on_container_copy_assignment`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `false_type`.|
|`propagate_on_container_move_assignment`|Dieser Typ ist `Alloc::propagate_on_container_move_assignment`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `false_type`. Wenn der Typ weiter gilt, kopiert ein zuweisungsfähiger Container seinen gespeicherten Allocator auf eine Bewegungszuweisung.|
|`propagate_on_container_swap`|Dieser Typ ist `Alloc::propagate_on_container_swap`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `false_type`. Wenn der Typ weiter gilt, tauscht ein zuweisungsfähiger Container seinen gespeicherten Allocator auf einem Swap aus.|
|`size_type`|Dieser Typ ist `Alloc::size_type`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `make_unsigned<difference_type>::type`.|
|`value_type`|Dieser Typ ist ein Synonym für `Alloc::value_type`.|
|`void_pointer`|Dieser Typ ist `Alloc::void_pointer`, wenn dieser Typ wohlgeformt ist; andernfalls ist dieser Typ `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Statische Methoden

Folgende statische Methoden rufen die entsprechenden Methoden auf einem vorhandenen Allocator-Parameter auf.

|Name|Beschreibung|
|-|-|
|[Jugend](#allocate)|Eine statische Methode, die mithilfe des vorhandenen Allocator-Parameters Arbeitsspeicher zuweist.|
|[Erstellen](#construct)|Eine statische Methode, die mithilfe eines angegebenen Allocators ein Objekt erstellt.|
|[DEALLOCATE](#deallocate)|Eine statische Methode, die mithilfe eines angegebenen Allocators eine angegebene Anzahl von Objekten freigibt.|
|[zerstören](#destroy)|Eine statische Methode, die mithilfe eines angegebenen Allocators den Destruktor in einem Objekt aufruft, ohne dass dessen Arbeitsspeicher freigegeben wird.|
|[max_size](#max_size)|Eine statische Methode, die mithilfe eines angegebenen Allocators die maximale Anzahl von zuweisbaren Objekten ermittelt.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Eine statische Methode, die `select_on_container_copy_construction` in einem angegebenen Allocator aufruft.|

### <a name="allocate"></a><a name="allocate"></a> Jugend

Eine statische Methode, die mithilfe des vorhandenen Allocator-Parameters Arbeitsspeicher zuweist.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

*Countdown*\
Die Anzahl der zuzuweisenden Elemente.

*deuteten*\
Ein `const_pointer`, der dem Zuweisungsobjekt möglicherweise dabei hilft, die Anforderung von Speicherplatz zu erfüllen. Dazu sucht er die Adresse eines vor der Anforderung zugewiesenen Objekts. Ein NULL-Zeiger wird nicht als Hinweis behandelt.

#### <a name="return-value"></a>Rückgabewert

Jede Methode gibt einen Zeiger auf das zugewiesene Objekt zurück.

Die erste statische Methode gibt `al.allocate(count)` zurück.

Die zweite Methode gibt dann `al.allocate(count, hint)` zurück, wenn der Ausdruck wohlgeformt ist; andernfalls `al.allocate(count)`.

### <a name="construct"></a><a name="construct"></a> Erstellen

Eine statische Methode, die mithilfe eines angegebenen Allocators ein Objekt erstellt.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

*PTR*\
Ein Zeiger auf den Speicherort, in dem das Objekt erstellt werden soll.

*args*\
Eine Liste von Argumenten, die an den Objektkonstruktor übergeben wird.

#### <a name="remarks"></a>Bemerkungen

Die statische Memberfunktion ruft `al.construct(ptr, args...)` auf, wenn der Ausdruck wohlgeformt ist; andernfalls wertet es `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)` aus.

### <a name="deallocate"></a><a name="deallocate"></a> DEALLOCATE

Eine statische Methode, die mithilfe eines angegebenen Allocators eine angegebene Anzahl von Objekten freigibt.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

*PTR*\
Ein Zeiger auf den Anfangsort der freizugebenden Objekte.

*Countdown*\
Die Anzahl der freizugebenden Objekte.

#### <a name="remarks"></a>Bemerkungen

Diese Methode ruft `al.deallocate(ptr, count)` auf.

Diese Methode löst keine Aktion aus.

### <a name="destroy"></a><a name="destroy"></a> zerstören

Eine statische Methode, die mithilfe eines angegebenen Allocators den Destruktor in einem Objekt aufruft, ohne dass dessen Arbeitsspeicher freigegeben wird.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

*PTR*\
Ein Zeiger auf den Speicherort des Objekts.

#### <a name="remarks"></a>Bemerkungen

Diese Methode ruft `al.destroy(ptr)` auf, wenn der Ausdruck wohlgeformt ist; andernfalls wertet es `ptr->~Uty()` aus.

### <a name="max_size"></a><a name="max_size"></a> max_size

Eine statische Methode, die mithilfe eines angegebenen Allocators die maximale Anzahl von zuweisbaren Objekten ermittelt.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

#### <a name="remarks"></a>Bemerkungen

Diese Methode gibt dann `al.max_size()` zurück, wenn der Ausdruck wohlgeformt ist; andernfalls `numeric_limits<size_type>::max()`.

### <a name="select_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a> select_on_container_copy_construction

Eine statische Methode, die `select_on_container_copy_construction` in einem angegebenen Allocator aufruft.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>Parameter

*irdische*\
Ein Zuweisungsobjekt.

#### <a name="return-value"></a>Rückgabewert

Diese Methode gibt zurück `al.select_on_container_copy_construction()` , wenn dieser Typ wohl geformt ist. andernfalls wird *Al*zurückgegeben.

#### <a name="remarks"></a>Bemerkungen

Diese Methode wird verwendet, um einen Allocator anzugeben, wenn der zugeordnete Container durch eine Kopie erstellt wurde.
