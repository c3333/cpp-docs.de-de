---
title: defaultvtable (com-Attribut C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 2da0d8070f961f1ae0fc075585eb28881f712fb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215256"
---
# <a name="defaultvtable"></a>defaultvtable

Definiert eine Schnittstelle als standardmäßige Vtable-Schnittstelle für ein COM-Objekt.

## <a name="syntax"></a>Syntax

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parameter

*interface*<br/>
Die angegebene Schnittstelle, für die die Standard-Vtable für das COM-Objekt festgelegt werden soll.

## <a name="remarks"></a>Bemerkungen

Das **defaultvtable** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut [defaultvtable](/windows/win32/Midl/defaultvtable) .

## <a name="example"></a>Beispiel

Der folgende Code zeigt Attribute für eine Klasse, die **defaultvtable** verwenden, um eine Standardschnittstelle anzugeben:

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
