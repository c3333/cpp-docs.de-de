---
title: Ref (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ref
helpviewer_keywords:
- ref attribute
ms.assetid: 67e82d3e-07d9-4ef8-bf2b-0a4491d12557
ms.openlocfilehash: 92b3c7b2cddf17a70a949914ef82540457696f20
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846107"
---
# <a name="ref-c"></a>ref (C++)

Bezeichnet einen Verweis Zeiger.

## <a name="syntax"></a>Syntax

```cpp
[ref]
```

## <a name="remarks"></a>Bemerkungen

Das **ref** C++-Attribut verfügt über die gleiche Funktionalität [wie das-](/windows/win32/Midl/ref) Attribut des Verweis-Attributs.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie das **ref** -Attribut verwendet wird:

```cpp
// cpp_attr_ref_ref.cpp
// compile with: /LD
#include <windows.h>
[module(name="ATLFIRELib")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1), unique] char * GetFirstName([in, ref] char * pszFullName );
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`typedef`**, Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)
