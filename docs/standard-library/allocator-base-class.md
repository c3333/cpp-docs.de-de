---
title: allocator_base-Klasse
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
ms.openlocfilehash: b55a7ec92787cb6b3103bf71b65d137d24ffff04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617584"
---
# <a name="allocator_base-class"></a>allocator_base-Klasse

Definiert die Basisklasse und allgemeine Funktionen, die zum Erstellen einer benutzerdefinierten Zuweisung von einem Synchronisierungsfilter erforderlich sind.

## <a name="syntax"></a>Syntax

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Type*|Der Elementtyp, die durch die Zuweisung zugeordnet wird.|
|*Synchron*|Die Synchronisierungsrichtlinie für die Zuweisung: [sync_none-Klasse](sync-none-class.md), [sync_per_container-Klasse](sync-per-container-class.md), [sync_per_thread-Klasse](sync-per-thread-class.md) oder [sync_shared-Klasse](sync-shared-class.md).|

### <a name="constructors"></a>Konstruktoren

|Konstruktor|Beschreibung|
|-|-|
|[allocator_base](#allocator_base)|Konstruiert ein Objekt vom Typ `allocator_base`.|

### <a name="typedefs"></a>TypeDefs

|Name des Typs|Beschreibung|
|-|-|
|[const_pointer](#const_pointer)|Ein Typ, der einen konstanten Zeiger auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.|
|[const_reference](#const_reference)|Ein Typ, der einen konstanten Verweis auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.|
|[difference_type](#difference_type)|Ein ganzzahliger Typ mit Vorzeichen, der die Differenz zwischen Werten von Zeigern und dem Typ des Objekts, das von der Zuweisung verwaltet wird, darstellen kann.|
|[Zeichner](#pointer)|Ein Typ, der einen Zeiger auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.|
|[Referenz](#reference)|Ein Typ, der einen Verweis auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.|
|[size_type](#size_type)|Ein ganzzahliger Typ ohne Vorzeichen, der die Länge einer beliebigen Sequenz darstellen kann, die ein Objekt vom Typ `allocator_base` zuordnen kann.|
|[value_type](#value_type)|Ein Typ, der von der Zuweisung verwaltet wird.|

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[_Charalloc](#charalloc)|Ordnet Speicher für ein Array vom Typ " **char**" zu.|
|[_Chardealloc](#chardealloc)|Gibt Speicher für das Array frei, das Elemente vom Typ **char**enthält.|
|[address](#address)|Sucht die Adresse eines Objekts, dessen Wert angegeben wird.|
|[allocate](#allocate)|Ordnet einen Speicherblock zu, der groß genug ist, um mindestens eine angegebene Anzahl von Elementen zu speichern.|
|[Erstellen](#construct)|Erstellt eine bestimmte Art von Objekt an einer bestimmten Adresse, die mit einem angegebenen Wert initialisiert wird.|
|[DEALLOCATE](#deallocate)|Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.|
|[zerstören](#destroy)|Ruft einen Objektdestruktor auf, ohne die Zuordnung des Speicherplatzes aufzuheben, an dem Objekt gespeichert wurde.|
|[max_size](#max_size)|Gibt die Anzahl der Elemente vom Typ *Type* zurück, die von einem Objekt der Klassenzuweisung zugeordnet werden konnten, bevor der freie Speicherplatz verbraucht ist.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a>Allocator_base:: _Charalloc

Ordnet Speicher für ein Array vom Typ " **char**" zu.

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*count*|Die Anzahl der zuzuweisenden Elemente im Array|

### <a name="return-value"></a>Rückgabewert

Zeiger auf das zugewiesene Objekt.

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird von Containers verwendet, wenn sie mit einem Compiler kompiliert wird, der Rebind nicht kompilieren kann. Es implementiert `_Charalloc` für die benutzerdefinierte allocator-Klasse, indem es das Ergebnis eines Aufrufs an die Funktion `allocate` des Synchronisationsfilters zurückgibt.

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a>Allocator_base:: _Chardealloc

Gibt Speicher für das Array frei, das Elemente vom Typ **char**enthält.

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ptr*|Ein Zeiger auf das erste Objekt, dessen Zuordnung zum Speicherplatz aufgehoben werden soll.|
|*count*|Die Anzahl von Objekten, deren Zuweisung zum Speicherplatz aufgehoben werden soll.|

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird von Containers verwendet, wenn sie mit einem Compiler kompiliert wird, der Rebind nicht kompilieren kann. Für die benutzerdefinierte allocator-Klasse implementiert es `_Chardealloc`, indem es das Ergebnis eines Aufrufs an die Funktion `deallocate` des Synchronisationsfilters zurückgibt. Der Zeiger ptr muss schon vorher für ein Zuweisungsobjekt, das gleich `*this` ist,von einen Aufruf an `_Charalloc` zurückgegeben worden sein, damit er ein Arrayobjekt der gleichen Größe und des gleichen Typs zuweisen kann. `_Chardealloc` löst nie eine Ausnahme aus.

## <a name="allocator_baseaddress"></a><a name="address"></a>Allocator_base:: Address

Sucht die Adresse eines Objekts, dessen Wert angegeben wird.

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>Parameter

*ster*\
Der konstante oder nicht konstante Wert des Objekts, nach dessen Adresse gesucht wird.

### <a name="return-value"></a>Rückgabewert

Ein konstanter oder nicht konstanter Zeiger auf ein Objekt mit konstantem bzw. nicht konstantem Wert.

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird für die benutzerdefinierte allocator-Klasse implementiert, indem `&val` zurückgegeben wird.

## <a name="allocator_baseallocate"></a><a name="allocate"></a>Allocator_base:: zuordnen

Ordnet einen Speicherblock zu, der groß genug ist, um mindestens eine angegebene Anzahl von Elementen zu speichern.

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*_Nx*|Die Anzahl der zuzuweisenden Elemente im Array|
|*_Hint*|Dieser Parameter wird ignoriert.|

### <a name="return-value"></a>Rückgabewert

Zeiger auf das zugewiesene Objekt.

### <a name="remarks"></a>Hinweise

Die Memberfunktion implementiert Speicherreservierung für die benutzerdefinierte allocator-Klasse, indem sie das Ergebnis eines Aufrufs an die Funktion `allocate` des Synchronisationsfilters des Typs „type“ `*` wenn `_Nx == 1` zurückgibt; andernfalls indem sie das Ergebnis eines Aufrufs an den Cast `operator new(_Nx * sizeof(Type))` des Typs „Type“ `*`.

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a>Allocator_base:: Allocator_base

Konstruiert ein Objekt vom Typ `allocator_base`.

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Richting*|Das zu kopierende Zuweisungsobjekt.|

### <a name="remarks"></a>Hinweise

Der erste Konstruktor erstellt eine [allocator_base](allocator-base-class.md)-Instanz. Der zweite Konstruktor erstellt eine `allocator_base`-Instanz, so dass jede `allocator_base<Type, _Sync>`-Instanz `a`, `allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`.

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a>Allocator_base:: const_pointer

Ein Typ, der einen konstanten Zeiger auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a>Allocator_base:: const_reference

Ein Typ, der einen konstanten Verweis auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a>Allocator_base:: Construct

Erstellt eine bestimmte Art von Objekt an einer bestimmten Adresse, die mit einem angegebenen Wert initialisiert wird.

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ptr*|Ein Zeiger auf den Speicherort, in dem das Objekt erstellt werden soll.|
|*ster*|Der Wert, mit dem das zu erstellende Objekt initialisiert werden soll.|

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird für die benutzerdefinierte allocator-Klasse implementiert, indem `new((void*)ptr Type(val)` aufgerufen wird.

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a>Allocator_base::d ezuordnen

Gibt eine angegebene Anzahl von Objekten im Speicher frei, beginnend an einer angegebenen Position.

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ptr*|Ein Zeiger auf das erste Objekt, dessen Zuordnung zum Speicherplatz aufgehoben werden soll.|
|*_Nx*|Die Anzahl von Objekten, deren Zuweisung zum Speicherplatz aufgehoben werden soll.|

### <a name="remarks"></a>Hinweise

Die Memberfunktion wird für die benutzerdefinierte allocator-Klasse implementiert, indem `deallocate(ptr)` im Synchronisationsfilter `Sync` wenn `_Nx == 1` aufgerufen wird; andernfalls Aufruf an `operator delete(_Nx * ptr)`.

## <a name="allocator_basedestroy"></a><a name="destroy"></a>Allocator_base::d estroy

Ruft einen Objektdestruktor auf, ohne die Zuordnung des Speicherplatzes aufzuheben, an dem Objekt gespeichert wurde.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ptr*|Ein Zeiger, der die Adresse des zu zerstörenden Objekts angibt.|

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird für die benutzerdefinierte allocator-Klasse implementiert, indem `ptr->~Type()` aufgerufen wird.

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a>Allocator_base::d ifference_type

Ein ganzzahliger Typ mit Vorzeichen, der die Differenz zwischen Werten von Zeigern und dem Typ des Objekts, das von der Zuweisung verwaltet wird, darstellen kann.

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a>Allocator_base:: max_size

Gibt die Anzahl der Elemente vom Typ `Type` zurück, die von einem Objekt der Klassenzuweisung zugeordnet werden konnten, bevor der freie Speicherplatz verbraucht ist.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen, die zugewiesen werden konnten.

### <a name="remarks"></a>Hinweise

Diese Memberfunktion wird für die benutzerdefinierte allocator-Klasse implementiert, indem `(size_t)-1 / sizeof(Type)` wenn `0 < (size_t)-1 / sizeof(Type)` zurückgegeben wird; andernfalls `1`.

## <a name="allocator_basepointer"></a><a name="pointer"></a>Allocator_base::p

Ein Typ, der einen Zeiger auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a>Allocator_base:: Reference

Ein Typ, der einen Verweis auf den Typ des Objekts bereitstellt, das von der Zuweisung verwaltet wird.

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a>Allocator_base:: size_type

Ein ganzzahliger Typ ohne Vorzeichen, der die Länge einer beliebigen Sequenz darstellen kann, die ein Objekt vom Typ `allocator_base` zuordnen kann.

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a>Allocator_base:: value_type

Ein Typ, der von der Zuweisung verwaltet wird.

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>Siehe auch

[\<allocators>](allocators-header.md)
