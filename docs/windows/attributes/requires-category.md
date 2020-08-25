---
title: requires_category (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: d566e74a9019259e526fa27aec26500e9ef3e1c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846003"
---
# <a name="requires_category"></a>requires_category

Gibt die erforderlichen Komponenten Kategorien der Zielklasse an.

## <a name="syntax"></a>Syntax

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parameter

*requires_category*<br/>
Die ID der erforderlichen Kategorie.

## <a name="remarks"></a>Bemerkungen

Das **requires_category** C++-Attribut gibt die für die Zielklasse erforderlichen Komponenten Kategorien an. Weitere Informationen finden Sie unter [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden.

## <a name="example"></a>Beispiel

Der folgende Code erfordert, dass das-Objekt die Steuerelement Kategorie implementiert.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
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

[COM-Attribute](com-attributes.md)<br/>
[implements_category](implements-category.md)
