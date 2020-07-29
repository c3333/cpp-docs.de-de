---
title: is_move_constructible-Klasse
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 5495ac39a98f5c194f19d28ba85a1d59f47dfbb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222380"
---
# <a name="is_move_constructible-class"></a>is_move_constructible-Klasse

Testet, ob der Typ mit einem Verschiebungs Vorgang erstellt werden kann.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der Typ, der ausgewertet werden soll.

## <a name="remarks"></a>Bemerkungen

Ein typprädikat, das zu ausgewertet **`true`** wird, wenn der Typ *T* mit einem Verschiebungs Vorgang erstellt werden kann. Dieses Prädikat entspricht `is_constructible<T, T&&>`. Ein Typ *T* , der keinen bewegungskonstruktor besitzt, aber über einen Kopierkonstruktor verfügt, der ein- `const T&` Argument akzeptiert, entspricht `std::is_move_constructible` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
