---
title: PTR (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.ptr
helpviewer_keywords:
- ptr attribute
ms.assetid: 95eaea57-a5be-45f6-a612-ba2c9bc4645a
ms.openlocfilehash: c01fe93d8c4092b3a4754b0c70ff161d66dfe49f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839867"
---
# <a name="ptr"></a>ptr

Legt einen Zeiger als vollständigen Zeiger fest.

## <a name="syntax"></a>Syntax

```cpp
[ptr]
```

## <a name="remarks"></a>Bemerkungen

Das Attribut " **ptr** C++" hat die gleiche Funktionalität wie das Attribut " [ptr](/windows/win32/Midl/ptr) -Attribut".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **ptr**finden Sie im Beispiel für [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenparameter, Schnittstellen Methode, **`typedef`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)
