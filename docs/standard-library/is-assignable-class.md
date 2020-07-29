---
title: is_assignable-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 2137f6bfb63e93da2c1367a21f608c113e80d196
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215724"
---
# <a name="is_assignable-class"></a>is_assignable-Klasse

Testet, ob ein Wert des `From`-Typs einem `To`-Typ zugewiesen werden kann.

## <a name="syntax"></a>Syntax

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parameter

*An*\
Der Typ des Objekts, das die Zuweisung empfängt.

*Von*\
Der Typ des Objekts, das den Wert bereitstellt.

## <a name="remarks"></a>Bemerkungen

Der ausgewertete Ausdruck `declval<To>() = declval<From>()` muss wohlgeformt sein. Sowohl `From` als auch `To` müssen komplette Typen, **`void`** oder Arrays mit unbekannter Grenze sein.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
