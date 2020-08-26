---
title: Dual (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dual
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
ms.openlocfilehash: 4cc974bef46a403cbdc5b290f623acb06f40722f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845405"
---
# <a name="dual"></a>dual

Fügt eine Schnittstelle in die IDL-Datei als duale Schnittstelle ein.

## <a name="syntax"></a>Syntax

```cpp
[dual]
```

## <a name="remarks"></a>Bemerkungen

Wenn das **Dual** C++-Attribut einer Schnittstelle vorangestellt wird, bewirkt dies, dass die Schnittstelle innerhalb des Bibliotheks Blocks in der generierten IDL-Datei platziert wird.

## <a name="example"></a>Beispiel

Der folgende Code ist ein Attribut Block, der **Dual** vor einer Schnittstellen Definition verwendet:

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([in] long nSize);
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`dispinterface`|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Attribute nach Verwendung](attributes-by-usage.md)<br/>
[Zollunion](custom-cpp.md)<br/>
[dispinterface](dispinterface.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
