---
title: nicht erweiterbar (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 2a1cd4d685e2fd141c6e11feaea488f44a884c80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214670"
---
# <a name="nonextensible"></a>nonextensible

Gibt an, dass die `IDispatch` Implementierung nur die Eigenschaften und Methoden enthält, die in der Schnittstellen Beschreibung aufgeführt sind, und kann zur Laufzeit nicht mit zusätzlichen Elementen erweitert werden.

## <a name="syntax"></a>Syntax

```cpp
[nonextensible]
```

## <a name="remarks"></a>Bemerkungen

Das **nonextensible** C++ -Attribut verfügt über die gleiche Funktionalität wie das [nicht erweiterbare](/windows/win32/Midl/nonextensible) Mittel l-Attribut.

Die Verwendung von " **nonextensible** " erfordert auch das [oleautomation](oleautomation.md) -Attribut.

## <a name="example"></a>Beispiel

Der folgende Code zeigt eine Verwendung des **nicht erweiterbaren** Attributs:

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**interface**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|`dual` und `oleautomation`oder `dispinterface`|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)
