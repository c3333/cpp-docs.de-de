---
title: Call_as (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: 755741faec6c0ba702d372ca8dee486edcb72ef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167332"
---
# <a name="call_as"></a>call_as

Ermöglicht, dass eine [lokale](local-cpp.md) Funktion einer Remote Funktion zugeordnet werden kann, sodass die lokale Funktion aufgerufen wird, wenn die Remote Funktion aufgerufen wird.

## <a name="syntax"></a>Syntax

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parameter

*Funktion*<br/>
Die lokale Funktion, die aufgerufen werden soll, wenn eine Remote Funktion aufgerufen wird.

## <a name="remarks"></a>Bemerkungen

Das **Call_as** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Call_as](/windows/win32/Midl/call-as) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie Sie mit **Call_as** eine nicht Remote fähige Funktion (`f1`) einer Remote fähigen Funktion (`Remf1`) zuordnen können:

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellenmethode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[local](local-cpp.md)
