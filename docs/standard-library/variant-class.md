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
ms.openlocfilehash: e34704b0ad8cf8fbaf8ee9514583f9597be40122
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215399"
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

|||
|-|-|
|[variant](#variant)|Konstruiert ein Objekt vom Typ `variant`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[emplace](#emplace)|Erstellt einen neuen enthaltenen Wert.|
|[Index](#index)|Gibt den Index eines enthaltenen Werts zurück.|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|Gibt zurück, **`false`** Wenn die Variante einen Wert enthält.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_eq)|Ersetzt die Variante durch eine Kopie einer anderen Variante.|

## <a name="emplace"></a><a name="emplace"></a>emplace

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

## <a name="index"></a><a name="index"></a>Sin

Gibt den Index eines enthaltenen Werts zurück.

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a>Konfigur

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

## <a name="operator"></a><a name="op_eq"></a>Operator =

Ersetzt die Variante durch eine Kopie einer anderen Variante.

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a>Wechsel

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a>valueless_by_exception

Gibt zurück, **`false`** Wenn die Variante einen Wert enthält.

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
