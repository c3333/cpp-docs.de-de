---
title: is_standard_layout-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: fba77be22796f3cb5495543d262dd270ac13d598
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560594"
---
# <a name="is_standard_layout-class"></a>is_standard_layout-Klasse

Testet, ob der Typ ein Standardlayout ist.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz dieses typprädikats ist "true", wenn die *typität* eine Klasse ist, die über ein Standardlayout von Element Objekten im Arbeitsspeicher verfügt, andernfalls "false".

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
