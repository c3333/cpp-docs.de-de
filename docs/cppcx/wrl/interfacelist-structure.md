---
title: InterfaceList-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213862"
---
# <a name="interfacelist-structure"></a>InterfaceList-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Schnittstellen Name; die erste Schnittstelle in der rekursiven Liste.

*U*<br/>
Ein Schnittstellen Name; die verbleibenden Schnittstellen in der rekursiven Liste.

## <a name="remarks"></a>Bemerkungen

Wird verwendet, um eine rekursive Liste von Schnittstellen zu erstellen.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`FirstT`|Synonym für den Vorlagen Parameter *T*.|
|`RestT`|Synonym für den Vorlagen Parameter *U*.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InterfaceList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
