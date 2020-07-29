---
title: conditional-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: 03ec6248ba3361622ad061ac3854a60995148f4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228374"
---
# <a name="conditional-class"></a>conditional-Klasse

Wählt einen von zwei Typen, abhängig von der angegebenen Bedingung.

## <a name="syntax"></a>Syntax

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Parameter

*B*\
Der Wert, der den ausgewählten Typ bestimmt.

*T1*\
Das Typergebnis, wenn B „true“ ist.

*T2*\
Das Typergebnis, wenn B „false“ ist.

## <a name="remarks"></a>Bemerkungen

Die Typdefinition für Vorlagen Elemente ergibt `conditional<B, T1, T2>::type` *T1* , wenn *b* ergibt **`true`** , und wird zu *T2* ausgewertet, wenn *b* als ausgewertet wird **`false`** .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](../standard-library/type-traits.md)
