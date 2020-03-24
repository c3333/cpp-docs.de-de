---
title: CompareStringOrdinal-Methode
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214096"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal-Methode

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Der erste zu vergleichende hstring.

*rhs*<br/>
Der zweite zu vergleichende hstring.

## <a name="return-value"></a>Rückgabewert

|value|Bedingung|
|-----------|---------------|
|-1|*LHS* ist kleiner als *RHS*.|
|0|*LHS* ist für *RHS*.|
|1|*LHS* ist größer als *RHS*.|

## <a name="remarks"></a>Bemerkungen

Vergleicht zwei angegebene hstring-Objekte und gibt eine ganze Zahl zurück, die ihre relative Position in einer Sortierreihenfolge angibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrappers::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Wrappers::Details-Namespace](microsoft-wrl-wrappers-details-namespace.md)
