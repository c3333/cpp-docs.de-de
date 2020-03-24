---
title: CloakedIid-Struktur
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 1cc9e79384bbf4aae44199c2f35331e3afd8fd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214109"
---
# <a name="cloakediid-structure"></a>CloakedIid-Struktur

Gibt dem `RuntimeClass`-, `Implements`-und `ChainInterfaces`-Vorlagen an, dass auf die angegebene Schnittstelle in der IID-Liste nicht zugegriffen werden kann.

## <a name="syntax"></a>Syntax

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die-Schnittstelle, die ausgeblendet ist (verdeckt).

## <a name="remarks"></a>Bemerkungen

Im folgenden finden Sie ein Beispiel dafür, wie **cloakediid** verwendet wird: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`T`

`CloakedIid`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
