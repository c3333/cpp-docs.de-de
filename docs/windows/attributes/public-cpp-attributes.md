---
title: Public (C++-Attribute) (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.public
helpviewer_keywords:
- public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
ms.openlocfilehash: 6a19a9a2718ad5f0e7ac59c71e9b4df6a7e92dd2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836906"
---
# <a name="public-c-attributes"></a>public (C++-Attribute)

Stellt sicher, dass eine typedef in die Typbibliothek wechselt, auch wenn in der IDL-Datei nicht auf Sie verwiesen wird.

## <a name="syntax"></a>Syntax

```cpp
[public]
```

## <a name="remarks"></a>Bemerkungen

Das **`public`** C++-Attribut verfügt über die gleiche Funktionalität wie das [öffentliche](/windows/win32/Midl/public) Mittel l-Attribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das- **`public`** Attribut verwendet wird:

```cpp
// cpp_attr_ref_public.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, public] typedef long MEMBERID;

[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]
__interface IFireTabCtrl : IDispatch
{
   [id(2)] long procedure ([in, optional] VARIANT i);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`typedef`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
