---
title: RemoveIUnknown-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213615"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine-Klasse.

## <a name="remarks"></a>Bemerkungen

Definiert einen Typ, der einem `IUnknown`basierten Typ entspricht, aber über nicht virtuelle `QueryInterface`-, `AddRef`-und `Release` Element Funktionen verfügt.

Standardmäßig stellen com-Methoden die Methoden Virtual `QueryInterface`, `AddRef`und `Release` bereit. Allerdings ist für `ComPtr` nicht der Aufwand von virtuellen Methoden erforderlich. `RemoveIUnknown` entfällt diesen mehr Aufwand, indem private, nicht virtuelle `QueryInterface`-, `AddRef`-und `Release`-Methoden bereitgestellt werden.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`ReturnType`|Ein Synonym für einen Typ, der dem Vorlagen Parameter *T* entspricht, jedoch nicht virtuelle `IUnknown` Member enthält.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** client.h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
