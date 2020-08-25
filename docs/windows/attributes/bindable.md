---
title: bindbare (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 27f44259401a42dcef7e2add370d95091d10879d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838970"
---
# <a name="bindable"></a>bindable

Gibt an, dass die Eigenschaft die Datenbindung unterstützt.

## <a name="syntax"></a>Syntax

```cpp
[bindable]
```

## <a name="remarks"></a>Bemerkungen

Das **bindbare** C++-Attribut verfügt über die gleiche Funktionalität wie das [binable](/windows/win32/Midl/bindable) -Attribut "Mittel l". Sie können Sie in Eigenschaften verwenden, die mit den Attributen [propget](propget.md), [PROPPUT](propput.md)oder [PROPPUTREF](propputref.md) definiert wurden, oder Sie können eine bindbare Methode manuell definieren.

Die folgenden MFC-Beispiele zeigen die Verwendung von **bindbaren**Elementen:

- [Steuerelemente Beispiele: MFC-basierte ActiveX-Steuerelemente](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [CIRC-Beispiel: ActiveX-Steuerelement](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [TESTHELP-Beispiel: ActiveX-Steuerelement mit Quick Infos und Hilfe](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie Sie **bindbare** für eine Eigenschaft verwenden können:

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenmethode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)
