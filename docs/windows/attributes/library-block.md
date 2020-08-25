---
title: library_block (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 13988abc12eb0b136dfc8d2c0d597005b56f0526
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834115"
---
# <a name="library_block"></a>library_block

Platziert ein Konstrukt innerhalb des IDL-Bibliotheks Blocks.

## <a name="syntax"></a>Syntax

```cpp
[library_block]
```

## <a name="remarks"></a>Bemerkungen

Wenn Sie ein Konstrukt innerhalb des Bibliotheks Blocks platzieren, stellen Sie sicher, dass es an die Typbibliothek übermittelt wird, unabhängig davon, ob darauf verwiesen wird. Standardmäßig werden nur durch die Attribute [Co-Klasse](coclass.md), [dispinterface](dispinterface.md)und [idl_module](idl-module.md) geänderte Konstrukte in den Bibliotheks Block eingefügt.

## <a name="example"></a>Beispiel

Im folgenden Code wird eine benutzerdefinierte Schnittstelle in den Bibliotheks Block eingefügt.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)
