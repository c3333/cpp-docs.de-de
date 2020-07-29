---
title: is_constructible-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: a968efa5a867a3fd0e60594784cdb11122a974b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222406"
---
# <a name="is_constructible-class"></a>is_constructible-Klasse

Testet, ob ein Typ konstruierbar ist, wenn die angegebenen Argumenttypen verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

*Args*\
Die Argument Typen, die in einem Konstruktor von *T*abgeglichen werden sollen.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist true, wenn der Typ *T* mit den Argument Typen in *args*konstruiert werden kann; andernfalls false. Der Typ *T* ist konstruierbar, wenn die Variablen Definition `T t(std::declval<Args>()...);` wohl geformt ist. Sowohl *T* als auch alle Typen in *args* müssen vollständige Typen sein, **`void`** oder Arrays mit unbekannter Grenze.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
