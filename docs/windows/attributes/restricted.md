---
title: eingeschränkt (C++ com-Attribut)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 0545c07936c59a59dd4712f4b0a2fd98a6701f2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230025"
---
# <a name="restricted"></a>restricted

Gibt an, dass ein Member eines Moduls, einer Schnittstelle oder einer dispinterface nicht willkürlich aufgerufen werden kann.

## <a name="syntax"></a>Syntax

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parameter

*interfaces*<br/>
Eine oder mehrere Schnittstellen, die möglicherweise nicht willkürlich für ein COM-Objekt aufgerufen werden. Dieser Parameter ist nur gültig, wenn er auf eine Klasse angewendet wird.

## <a name="remarks"></a>Bemerkungen

Das **restricted** C++-Attribut verfügt über die gleiche Funktionalität wie das [Eingeschränkte](/windows/win32/Midl/restricted) Mittel l-Attribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung des **eingeschränkten** Attributs:

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|Schnittstellen Methode, **Schnittstelle**, **`class`** ,**`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**Co-Klasse** (bei Anwendung auf **`class`** oder **`struct`** )|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)
