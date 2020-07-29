---
title: Switch_type (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: 13ea76e1153e1a42fd41fe0c087a7c7f15416760
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211930"
---
# <a name="switch_type"></a>switch_type

Identifiziert den Typ der Variablen, die als uniondiskriminant verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parameter

*type*<br/>
Der Switchtyp kann ein Integer-, Zeichen-, boolescher oder Enumerationstyp sein.

## <a name="remarks"></a>Bemerkungen

Das **Switch_type** C++-Attribut verfügt über die gleiche Funktionalität wie das [Switch_type](/windows/win32/Midl/switch-type) -Attribut "Mittel".

C++-Attribute unterstützen keine [gekapselten Unions](/windows/win32/Midl/encapsulated-unions). [Nicht gekapselte Unions](/windows/win32/Midl/nonencapsulated-unions) werden nur in der folgenden Form unterstützt:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Switch_type**finden Sie im [Fall](case-cpp.md) Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`typedef`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Exports](export.md)
