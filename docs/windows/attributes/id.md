---
title: ID (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: f67bf21fbe0040884cba4a54ed8d2a230cb20cd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830552"
---
# <a name="id"></a>id

Gibt einen *DISPID-* Parameter für eine Element Funktion an (entweder eine Eigenschaft oder eine Methode in einer Schnittstelle oder einer dispinterface).

## <a name="syntax"></a>Syntax

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID für die Schnittstellen Methode.

## <a name="remarks"></a>Bemerkungen

Das **ID** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut der [ID](/windows/win32/Midl/id) -Mitte.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung der **ID**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenmethode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Datenmember-Attribute](data-member-attributes.md)<br/>
[DefaultValue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)
