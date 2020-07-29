---
title: beliebige Klasse
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 66e74a7fa7f35aae9ac9e1f3ba7520e8d3f9b3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203961"
---
# <a name="any-class"></a>beliebige Klasse

Speichert eine Instanz eines beliebigen Typs, der den konstruktoranforderungen entspricht, oder es ist kein Wert vorhanden, der als Zustand der Klasse beliebiges Objekt bezeichnet wird.

Die gespeicherte Instanz wird als enthaltener Wert bezeichnet. Zwei Zustände sind identisch, wenn beide entweder keinen Wert haben oder beide einen Wert aufweisen und die enthaltenen Werte identisch sind.

## <a name="syntax"></a>Syntax

```cpp
class any
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[irgendeiner](#any)|Konstruiert ein Objekt vom Typ `any`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[emplace](#emplace)|Legt einen beliebigen Wert fest.|
|[has_value](#has_value)|Gibt zurück, **`true`** Wenn ein beliebiger einen Wert aufweist.|
|[reset](#reset)|Setzt eine beliebige zurück.|
|[swap](#swap)|Tauscht zwei beliebige-Objekte aus.|
|[type](#type)|Gibt den beliebigen Typ zurück.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_eq)|Ersetzt alle durch eine Kopie einer anderen.|

## <a name="any"></a><a name="any"></a>irgendeiner

Konstruiert ein Objekt vom Typ `any`. Schließt außerdem einen Dekonstruktor ein.

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a><a name="emplace"></a>emplace

Legt einen beliebigen Wert fest.

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a><a name="has_value"></a>has_value

Gibt zurück, **`true`** Wenn ein beliebiger einen Wert aufweist.

```cpp
bool has_value() const noexcept;
```

## <a name="operator"></a><a name="op_eq"></a>Operator =

Ersetzt alle durch eine Kopie einer anderen.

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die, die in alle kopiert werden.

## <a name="reset"></a><a name="reset"></a>Festlegen

Setzt eine beliebige zurück.

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a>Wechsel

Tauscht zwei beliebige-Objekte aus.

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a><a name="type"></a>-Typ

Gibt den beliebigen Typ zurück.

```cpp
const type_info& type() const noexcept;
```
