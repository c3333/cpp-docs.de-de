---
title: DerefHelper-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 43453d3162de697fa1cfcf0581953c91bbe3934f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214044"
---
# <a name="derefhelper-structure"></a>DerefHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Vorlagen Parameter.

## <a name="remarks"></a>Bemerkungen

Stellt einen dereferenzierten Zeiger auf den `T*` Template-Parameter dar.

**Derefhelper** wird in einem Ausdruck wie z. b.: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`verwendet.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`DerefType`|Der Bezeichner für den dereferenzierten Vorlagen Parameter `T*`.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`DerefHelper`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
