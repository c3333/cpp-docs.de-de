---
title: pragma (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: e5683a6f52eccf9eae7c29010849a148e506b286
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836168"
---
# <a name="pragma"></a>pragma

Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten IDL-Datei aus.

## <a name="syntax"></a>Syntax

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>Parameter

*pragma_statement*<br/>
Das Pragma, das in der generierten IDL-Datei gespeichert werden soll.

## <a name="remarks"></a>Bemerkungen

Das **pragma** C++-Attribut verfügt über die gleiche Funktionalität wie das [pragma](/windows/win32/Midl/pragma) -Attribut "Mittel".

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)
