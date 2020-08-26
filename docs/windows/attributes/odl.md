---
title: ODL (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: a2f3c58e40dc14d256ca694bb1266aed13dc9620
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842818"
---
# <a name="odl"></a>odl

Identifiziert eine Schnittstelle als Object Description Language (ODL)-Schnittstelle. Der mittlerer l-Compiler benötigt das **ODL** -Attribut nicht. Sie wird nur aus Gründen der Kompatibilität mit älteren ODL-Dateien erkannt.

## <a name="syntax"></a>Syntax

```cpp
[odl]
```

## <a name="remarks"></a>Bemerkungen

Das **ODL** -C++-Attribut verfügt über die gleiche Funktionalität wie das [ODL](/windows/win32/Midl/odl) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)
