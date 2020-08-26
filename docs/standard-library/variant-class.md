---
title: Variant-Klasse
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: aba121604636ebd253523acb9b630dd9ab762584
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840023"
---
# <a name="variant-class"></a>Variant-Klasse

Jede Instanz von Variant zu einem beliebigen Zeitpunkt enthält entweder einen Wert von einem der alternativen Typen oder hat keinen Wert.

## <a name="syntax"></a>Syntax

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[variant](#variant)|Konstruiert ein Objekt vom Typ `variant`.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[emplace](#emplace)|Erstellt einen neuen enthaltenen Wert.|
|[Index](#index)|Gibt den Index eines enthaltenen Werts zurück.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Gibt zurück, **`false`** Wenn die Variante einen Wert enthält.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator =](#op_eq)|Ersetzt die Variante durch eine Kopie einer anderen Variante.|

## <a name="emplace"></a><a name="emplace"></a> emplace

Erstellt einen neuen enthaltenen Wert.

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a><a name="index"></a> Sin

Gibt den Index eines enthaltenen Werts zurück.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> Konfigur

Konstruiert ein Objekt vom Typ `variant`. Schließt außerdem einen Dekonstruktor ein.

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>Parameter

*Irdische*\
Die mit diesem Objekt zu verwendende Zuweisungsklasse.

## <a name="operator"></a><a name="op_eq"></a> Operator =

Ersetzt die Variante durch eine Kopie einer anderen Variante.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> Wechsel

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

Gibt zurück, **`false`** Wenn die Variante einen Wert enthält.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
