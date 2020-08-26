---
title: aggregierbare (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 6782b1ca28eb07b3f726bd85cd7fffa9b1f1bad2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836373"
---
# <a name="aggregatable"></a>aggregatable

Gibt an, dass die Klasse Aggregationen unterstützt.

## <a name="syntax"></a>Syntax

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parameter

*value*<br/>
Optionale Ein Parameter, der angibt, wann das COM-Objekt aggregiert werden kann:

- `never` Das COM-Objekt kann nicht aggregiert werden.

- `allowed` Das COM-Objekt kann direkt erstellt oder aggregiert werden. Dies ist die Standardoption.

- `always` Das COM-Objekt kann nicht direkt erstellt werden und kann nur aggregiert werden. Wenn Sie `CoCreateInstance` für dieses Objekt aufzurufen, müssen Sie die-Schnittstelle des Aggregations Objekts `IUnknown` (das steuernde `IUnknown` ) angeben.

## <a name="remarks"></a>Bemerkungen

Das Attribut " **aggregierbare** C++" verfügt über die gleiche Funktionalität wie das Attribut " [aggregierbare](/windows/win32/Midl/aggregatable) ". Dies bedeutet, dass der Compiler das Attribut " **aggregierbare** " über an die generierte IDL-Datei übergibt.

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden. Wenn ein einzelnes Attribut verwendet wird, werden die anderen beiden automatisch angewendet. Wenn z. b `progid` . angewendet wird `vi_progid` , `coclass` werden auch und angewendet.

### <a name="atl-projects"></a>ATL-Projekte

Wenn dieses Attribut in einem Projekt verwendet wird, das ATL verwendet, ändert sich das Verhalten des Attributs. Zusätzlich zu dem zuvor beschriebenen Verhalten fügt das-Attribut der Zielklasse auch eines der folgenden Makros hinzu:

|Parameterwert|Makro eingefügt|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
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

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Aggregation](/windows/win32/com/aggregation)
