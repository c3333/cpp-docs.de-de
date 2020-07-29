---
title: is_trivially_assignable-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 14a3ee638bd6df3b52e7327ca6e3c77f4a0e8b71
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224863"
---
# <a name="is_trivially_assignable-class"></a>is_trivially_assignable-Klasse

Testet, ob ein Wert des `From`-Typs einem `To`-Typ trivial zugewiesen werden kann.

## <a name="syntax"></a>Syntax

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parameter

*An*\
Der Typ des Objekts, das die Zuweisung empfängt.

*Von*\
Der Typ des Objekts, das den Wert bereitstellt.

## <a name="remarks"></a>Bemerkungen

Der Ausdruck `declval<To>() = declval<From>()` muss wohlgeformt sein, und es muss für den Compiler bekannt sein, dass er keine nicht trivialen Vorgänge benötigt. Sowohl `From` als auch `To` müssen komplette Typen, **`void`** oder Arrays mit unbekannter Grenze sein.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)
