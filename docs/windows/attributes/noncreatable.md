---
title: nicht in die Tabelle (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: b645d6d6cbcaeff346437d6457360ecdef8d3190
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840556"
---
# <a name="noncreatable"></a>noncreatable

Definiert ein Objekt, das nicht allein instanziiert werden kann.

## <a name="syntax"></a>Syntax

```cpp
[noncreatable]
```

## <a name="remarks"></a>Bemerkungen

Das **nicht** Erstell Bare C++-Attribut verfügt über die gleiche Funktionalität wie das [nicht](/windows/win32/Midl/noncreatable) Erstell Bare-Attribut "Mittel l" und wird automatisch an den generierten übergeben. IDL-Datei durch den Compiler.

Wenn dieses Attribut in einem Projekt verwendet wird, das ATL verwendet, ändert sich das Verhalten des Attributs. Zusätzlich zum obigen Verhalten fügt das Attribut auch das [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) Makro ein. Dieses Makro zeigt ATL an, dass das Objekt nicht extern erstellt werden kann.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
