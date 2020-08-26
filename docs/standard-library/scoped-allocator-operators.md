---
title: '&lt;scoped_allocator&gt;-Header'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 907772069c192b3ef75c7366e079b1da1dd36f8d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846250"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt;-Header

[Operator! =](#op_neq)\
[Operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> Operator! =

Überprüft zwei `scoped_allocator_adaptor`-Objekte auf Ungleichheit.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parameter

*linken*\
Das linke `scoped_allocator_adaptor`-Objekt.

*Richting*\
Das rechte `scoped_allocator_adaptor`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a> Operator = =

Überprüft zwei `scoped_allocator_adaptor`-Objekte auf Gleichheit.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parameter

*linken*\
Das linke `scoped_allocator_adaptor`-Objekt.

*Richting*\
Das rechte `scoped_allocator_adaptor`-Objekt.

### <a name="return-value"></a>Rückgabewert

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Weitere Informationen

[<scoped_allocator>](../standard-library/scoped-allocator.md)
