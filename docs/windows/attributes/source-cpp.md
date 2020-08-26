---
title: Quelle (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.source
helpviewer_keywords:
- source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
ms.openlocfilehash: f9a1f576e26805c5dd84c2d83cdf3615d0661af3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842766"
---
# <a name="source-c"></a>source (C++)

Gibt für eine Klasse die Quell Schnittstellen der COM-Objekte für Verbindungspunkte an. Gibt für eine Eigenschaft oder Methode an, dass der Member ein Objekt oder eine Variante zurückgibt, das eine Quelle von Ereignissen ist.

## <a name="syntax"></a>Syntax

```cpp
[ source(interfaces) ]
```

### <a name="parameters"></a>Parameter

*interfaces*<br/>
Eine oder mehrere Schnittstellen, die Sie angeben, wenn Sie das Quell Attribut auf eine Klasse anwenden. Dieser Parameter wird nicht verwendet, wenn die Quelle auf eine Eigenschaft oder Methode angewendet wird.

## <a name="remarks"></a>Bemerkungen

Das **Source** C++-Attribut verfügt über die gleiche Funktionalität wie das- [Quell](/windows/win32/Midl/source) Attribut.

Sie können das [default](default-cpp.md) -Attribut verwenden, um die standardmäßige Quell Schnittstelle für ein Objekt anzugeben.

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_source.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT get_I([out, retval]long *i);
};

[object, uuid(11111111-1111-1111-1111-111111111131)]
__interface c
{
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]
   HRESULT et_I([out, retval]long *i);
};

[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]
class N : public b
{
};

[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]
class NN : public b
{
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**`class`**, **`struct`** ,- **Schnittstelle**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|`coclass` (bei Anwendung auf Klasse oder Struktur)|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[coclass](coclass.md)
