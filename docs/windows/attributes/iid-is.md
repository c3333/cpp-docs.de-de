---
title: iid_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 6a8fe8c7481cd251baff65293607733573f46ea6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832216"
---
# <a name="iid_is"></a>iid_is

Gibt die IID der COM-Schnittstelle an, auf die durch einen Schnittstellen Zeiger gezeigt wird.

## <a name="syntax"></a>Syntax

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Ein C-sprach Ausdruck, der eine IID einer COM-Schnittstelle angibt, auf die von einem Schnittstellen Zeiger gezeigt wird.

## <a name="remarks"></a>Bemerkungen

Das **iid_is** C++-Attribut verfügt über die gleiche Funktionalität wie das [iid_is](/windows/win32/Midl/iid-is) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung von **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenparameter, Datenmember|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)
