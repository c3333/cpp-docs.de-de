---
title: Async_uuid (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 537bd6d645532d9d5d20b740125c66f3953239bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168459"
---
# <a name="async_uuid"></a>async_uuid

Gibt die UUID an, die den mittlerer l-Compiler anweist, sowohl synchrone als auch asynchrone Versionen einer COM-Schnittstelle zu definieren.

## <a name="syntax"></a>Syntax

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>Parameter

*uuid*<br/>
Ein UUID-Wert, der die Version der Schnittstelle identifiziert.

## <a name="remarks"></a>Bemerkungen

Das **Async_uuid** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Async_uuid](/windows/win32/Midl/async-uuid) -Attribut "Mittel".

## <a name="example"></a>Beispiel

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|`interface`|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|**Dual**, **dispinterface**|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)
