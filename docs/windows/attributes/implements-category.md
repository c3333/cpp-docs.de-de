---
title: Implements_category (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: cd9a4de8834bc22368393e9ea4639884785af0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846120"
---
# <a name="implements_category"></a>implements_category

Gibt die von der Zielklasse implementierten Komponenten Kategorien an.

## <a name="syntax"></a>Syntax

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>Parameter

*implements_category*<br/>
Die ID der implementierten Kategorie.

## <a name="remarks"></a>Bemerkungen

Das **Implements_category** C++-Attribut gibt die von der Zielklasse implementierten Komponenten Kategorien an. Dies erfolgt durch Erstellen einer Kategoriezuordnung und Hinzufügen von separaten Einträgen, die durch das **Implements_category** -Attribut angegeben werden. Weitere Informationen finden Sie unter [Komponenten Kategorien und Funktionsweise](/windows/win32/com/component-categories-and-how-they-work).

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden. Wenn ein einzelnes Attribut verwendet wird, werden die anderen beiden automatisch angewendet. Wenn z. b `progid` . angewendet wird `vi_progid` , `coclass` werden auch und angewendet.

## <a name="example"></a>Beispiel

Der folgende Code gibt an, dass das folgende-Objekt die- `Control` Kategorie implementiert.

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Ja|
|**Erforderliche Attribute**|Eines der folgenden: `coclass` , `progid` oder `vi_progid`|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)
