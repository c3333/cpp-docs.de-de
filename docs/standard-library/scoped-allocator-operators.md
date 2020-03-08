---
title: '&lt;scoped_allocator&gt;-Header'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 071fc3b73cd3378b110d6d412bb7575e35a77478
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876334"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator&gt;-Header

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Überprüft zwei `scoped_allocator_adaptor`-Objekte auf Ungleichheit.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `scoped_allocator_adaptor`-Objekt.

*Rechte*\
Das rechte `scoped_allocator_adaptor`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(left == right)`

## <a name="op_eq_eq"></a> operator==

Überprüft zwei `scoped_allocator_adaptor`-Objekte auf Gleichheit.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parameter

*Linker*\
Das linke `scoped_allocator_adaptor`-Objekt.

*Rechte*\
Das rechte `scoped_allocator_adaptor`-Objekt.

### <a name="return-value"></a>Rückgabewert

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Weitere Informationen

[<scoped_allocator>](../standard-library/scoped-allocator.md)
