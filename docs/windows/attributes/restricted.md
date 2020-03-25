---
title: eingeschränkt (C++ com-Attribut)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: a47c56673e19f891b24ff433b9c614804f0bd51c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166366"
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

*Web*<br/>
Eine oder mehrere Schnittstellen, die möglicherweise nicht willkürlich für ein COM-Objekt aufgerufen werden. Dieser Parameter ist nur gültig, wenn er auf eine Klasse angewendet wird.

## <a name="remarks"></a>Bemerkungen

Das **restricted** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Eingeschränkte](/windows/win32/Midl/restricted) Mittel l-Attribut.

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
|**Betrifft**|Schnittstellen Methode, **Schnittstelle**, **Klasse**, **Struktur**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|**Co-Klasse** (bei Anwendung auf **Klasse** oder **Struktur**)|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[Methodenattribut](method-attributes.md)
