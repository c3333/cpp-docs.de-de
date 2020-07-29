---
title: Is_nothrow_constructible-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: e52b16965d849f992731c4ff4254fd218b944269
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217752"
---
# <a name="is_nothrow_constructible-class"></a>Is_nothrow_constructible-Klasse

Testet, ob ein Typ konstruierbar ist, und nicht ausgelöst wird, wenn angegebene Argumenttypen verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

*Args*\
Die Argument Typen, die in einem Konstruktor von *T*abgeglichen werden sollen.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn der Typ *T* mit den Argument Typen in *args*konstruiert werden kann und der Konstruktor vom Compiler nicht ausgelöst werden kann. Andernfalls enthält Sie false. Der Typ *T* ist konstruierbar, wenn die Variablen Definition `T t(std::declval<Args>()...);` wohl geformt ist. Sowohl *T* als auch alle Typen in *args* müssen vollständige Typen sein, **`void`** oder Arrays mit unbekannter Grenze.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
