---
title: Swap-Funktion (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: e665dbca025da56ba81c3fdf1749b2d653b78c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213563"
---
# <a name="swap-function-wrl"></a>Swap-Funktion (WRL)

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>Parameter

*left*<br/>
Das erste Argument.

*right*<br/>
Das zweite Argument.

## <a name="return-value"></a>Rückgabewert

## <a name="remarks"></a>Bemerkungen

Tauscht die Werte der beiden angegebenen Argumente aus.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
