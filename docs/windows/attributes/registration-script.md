---
title: Registration_script (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 8a57f0b3d0925d1e1096a31734fa4c9d666c5743
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846081"
---
# <a name="registration_script"></a>registration_script

Führt das angegebene benutzerdefinierte Registrierungs Skript aus.

## <a name="syntax"></a>Syntax

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parameter

*script*<br/>
Der vollständige Pfad zu einer benutzerdefinierten Registrierungs Skriptdatei (. rgs). Der Wert **None**(z. b.) gibt an, `script = "none"` dass die Co-Klasse keine Registrierungsanforderungen hat.

## <a name="remarks"></a>Bemerkungen

Das **Registration_script** C++-Attribut führt das durch das *Skript*angegebene benutzerdefinierte Registrierungs Skript aus. Wenn dieses Attribut nicht angegeben wird, wird eine RGS-Standarddatei (die Informationen zum Registrieren der Komponente enthält) verwendet. Weitere Informationen zu RGS-Dateien finden Sie in [der ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente)](../../atl/atl-registry-component-registrar.md).

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden.

## <a name="example"></a>Beispiel

Der folgende Code gibt an, dass die Komponente über ein Registrierungs Skript mit dem Namen cpp_attr_ref_registration_script. RGS verfügt.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Eine oder mehrere der folgenden: `coclass` , `progid` oder `vi_progid` .|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[RDX](rdx.md)
