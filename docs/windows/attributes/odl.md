---
title: ODL (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: 2627be876f0c46bb7d72c2c6b825cf76e24b1eb1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214733"
---
# <a name="odl"></a>odl

Identifiziert eine Schnittstelle als Object Description Language (ODL)-Schnittstelle. Der mittlerer l-Compiler benötigt das **ODL** -Attribut nicht. Sie wird nur aus Gründen der Kompatibilität mit älteren ODL-Dateien erkannt.

## <a name="syntax"></a>Syntax

```cpp
[odl]
```

## <a name="remarks"></a>Bemerkungen

Das **ODL** C++ -Attribut verfügt über die gleiche Funktionalität wie das [ODL](/windows/win32/Midl/odl) -Attribut "Mittel l".

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

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**interface**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)
