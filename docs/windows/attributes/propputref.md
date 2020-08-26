---
title: propputref (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: dbb5d5966fc82f69be0ed7d2fa0a66ad558a7915
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839906"
---
# <a name="propputref"></a>propputref

Gibt eine Eigenschafts Einstellungs Funktion an, die einen Verweis anstelle eines Werts verwendet.

## <a name="syntax"></a>Syntax

```cpp
[propputref]
```

## <a name="remarks"></a>Bemerkungen

Das **PROPPUTREF** C++-Attribut verfügt über die gleiche Funktionalität wie das [PROPPUTREF](/windows/win32/Midl/propputref) -Attribut "mittlerl".

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **PROPPUTREF**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`propget`, `propput`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
