---
title: Propget (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 2627213d1d1dc74edb33d70ac45f3b7bbd38ba6b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839971"
---
# <a name="propget"></a>propget

Gibt eine eigenschaftenaccessorfunktion an.

## <a name="syntax"></a>Syntax

```cpp
[propget]
```

## <a name="remarks"></a>Bemerkungen

Das **propget** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut von [propget](/windows/win32/Midl/propget) .

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **propget finden Sie**im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`propput`, `propputref`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)
