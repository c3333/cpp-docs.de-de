---
title: Transmit_as (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.transmit_as
helpviewer_keywords:
- transmit_as attribute
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
ms.openlocfilehash: cf89be12672ac77a67617b6b222f27d739db9261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214486"
---
# <a name="transmit_as"></a>transmit_as

Weist den Compiler an, einen dargestellten Typ, den Client-und Server Anwendungen manipulieren, mit einem übertragenen Typ zuzuordnen.

## <a name="syntax"></a>Syntax

```cpp
[ transmit_as(type) ]
```

### <a name="parameters"></a>Parameter

*type*<br/>
Gibt den Datentyp an, der zwischen Client und Server übertragen wird.

## <a name="remarks"></a>Bemerkungen

Das **Transmit_as** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Transmit_as](/windows/win32/Midl/transmit-as) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt die Verwendung des **Transmit_as** -Attributs:

```cpp
// cpp_attr_ref_transmit_as.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export] typedef struct _TREE_NODE_TYPE {
unsigned short data;
struct _TREE_NODE_TYPE * left;
struct _TREE_NODE_TYPE * right;
} TREE_NODE_TYPE;

[export] struct PACKED_NODE {
   unsigned short data;   // same as normal node
   int index;   // array index of parent
};

// A left node recursive built array of
// the nodes in the tree.  Can be unpacked with
// that knowledge
[export] typedef struct _TREE_XMIT_TYPE {
   int count;
   [size_is(count)] PACKED_NODE node[];
} TREE_XMIT_TYPE;

[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;
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
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)
