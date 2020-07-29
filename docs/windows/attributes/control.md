---
title: Control (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.control
helpviewer_keywords:
- Control attribute
ms.assetid: 3d046bb2-4afe-4cb8-a762-233b296e1975
ms.openlocfilehash: 59f1a6d1ad940f79693f9c5e37c1fe6527da3805
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224460"
---
# <a name="control"></a>Steuerelement

Gibt an, dass der benutzerdefinierte Typ ein Steuerelement ist.

## <a name="syntax"></a>Syntax

```cpp
[control]
```

## <a name="remarks"></a>Bemerkungen

Das Attribut " **Control** " impliziert das [Co-Klasse](coclass.md) -Attribut. Das **Control** C++-Attribut verfügt über die gleiche Funktionalität [wie das-](/windows/win32/Midl/control) Attribut "Mittel l".

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_control.cpp
// compile with: /LD
#include <windows.h>
[module(name="Test", control=true)];

[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[coclass, control, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CTest : public ICustom {};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
