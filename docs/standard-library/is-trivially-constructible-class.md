---
title: Is_trivially_constructible-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 1f835dd348c6ef7f2ca7cd01f04c5afc059a55b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222328"
---
# <a name="is_trivially_constructible-class"></a>Is_trivially_constructible-Klasse

Testet, ob ein Typ trivial konstruierbar ist, wenn die angegebenen Argumenttypen verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

*Args*\
Die Argument Typen, die in einem Konstruktor von *T*abgeglichen werden sollen.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn der Typ *T* mit den Argument Typen in *args*trivial konstruiert werden kann; andernfalls "false". Typ *T* ist trivial konstruierbar, wenn die Variablen Definition `T t(std::declval<Args>()...);` wohl geformt ist und bekanntermaßen keine nicht trivialen Vorgänge aufruft. Sowohl *T* als auch alle Typen in *args* müssen vollständige Typen sein, **`void`** oder Arrays mit unbekannter Grenze.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
