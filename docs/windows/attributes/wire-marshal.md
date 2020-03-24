---
title: Wire_marshal (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.wire_marshal
helpviewer_keywords:
- wire_marshal attribute
ms.assetid: 244f9d72-776d-4ebd-b60a-cee600a126b5
ms.openlocfilehash: 0bf6b2ab353b8ad8866de5b2c7c79959306ee954
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215227"
---
# <a name="wire_marshal"></a>wire_marshal

Gibt einen Datentyp an, der anstelle eines anwendungsspezifischen Datentyps für die Übertragung verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
[wire_marshal]
```

## <a name="remarks"></a>Bemerkungen

Das **Wire_marshal** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Wire_marshal](/windows/win32/Midl/wire-marshal) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung von **Wire_marshal**:

```cpp
// cpp_attr_ref_wire_marshal.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export, public] typedef unsigned long _FOUR_BYTE_DATA;

[export] typedef struct _TWO_X_TWO_BYTE_DATA {
   unsigned short low;
   unsigned short high;
} TWO_X_TWO_BYTE_DATA ;

[export, wire_marshal(TWO_X_TWO_BYTE_DATA)] typedef _FOUR_BYTE_DATA FOUR_BYTE_DATA;
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**typedef**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
