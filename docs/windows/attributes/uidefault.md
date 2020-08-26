---
title: Uidefault (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uidefault
helpviewer_keywords:
- uidefault attribute
ms.assetid: 200de0e0-2e34-40a2-bae4-8d485a62264d
ms.openlocfilehash: 70f54c9d3e6aaa46aef08d109e8682989e382120
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843065"
---
# <a name="uidefault"></a>uidefault

Gibt an, dass der Typinformationsmember der Standard Member für die Anzeige in der Benutzeroberfläche ist.

## <a name="syntax"></a>Syntax

```cpp
[uidefault]
```

## <a name="remarks"></a>Bemerkungen

Das **Uidefault** C++-Attribut verfügt über die gleiche Funktionalität wie das [Uidefault](/windows/win32/Midl/uidefault) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt ein Beispiel für **Uidefault**:

```cpp
// cpp_attr_ref_uidefault.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom{
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   [uidefault]HRESULT id0([in] long l);
   [uidefault]HRESULT id1([in] long l);

   [uidefault, propget] HRESULT get_y(int *y);
   [uidefault, propput] HRESULT put_y(int y);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenmethode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)
