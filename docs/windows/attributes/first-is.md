---
title: First_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.first_is
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
ms.openlocfilehash: 1a06206d7df4dace3f749fdc8ceae7f68aaf095c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845262"
---
# <a name="first_is"></a>first_is

Gibt den Index des ersten Array Elements an, das übertragen werden soll.

## <a name="syntax"></a>Syntax

```cpp
[ first_is("expression") ]
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Mindestens ein C-sprach Ausdruck. Leere Argument Slots sind zulässig.

## <a name="remarks"></a>Bemerkungen

Das **First_is** C++-Attribut verfügt über die gleiche Funktionalität wie das [First_is](/windows/win32/Midl/first-is) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt verschiedene Möglichkeiten zum Angeben eines Abschnitts in einem Array:

```cpp
// cpp_attr_ref_first_is.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"

[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind,
requestedit] HRESULT get_I([out, retval]long *i);
   HRESULT Proc1([in] short First, [in] short Last,
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);
   HRESULT Proc2([in] short First, [in] short Last,
[last_is(First), size_is(Last)] char Arr2[]);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Feld in **`struct`** oder **`union`** , Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
