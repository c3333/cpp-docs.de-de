---
title: schreibgeschützt (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: ea2b0a46d34fc415a3b9eca97b92cda764fc7d42
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839802"
---
# <a name="readonly-c"></a>readonly (C++)

Verhindert die Zuweisung zu einem Datenelement

## <a name="syntax"></a>Syntax

```cpp
[readonly]
```

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut **readonly** hat die gleiche Funktion wie das MIDL-Attribut [readonly](/windows/win32/Midl/readonly) .

Wenn Sie die Änderung eines Methodenparameters verhindern möchten, verwenden Sie das [in](in-cpp.md) -Attribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung des **readonly** -Attributs:

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenmethode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Datenmember-Attribute](data-member-attributes.md)
