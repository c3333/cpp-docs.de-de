---
title: oleautomation (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 47842454ce52c65cf71a317f39a7649b0f9dd27d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842181"
---
# <a name="oleautomation"></a>oleautomation

Gibt an, dass eine Schnittstelle mit Automation kompatibel ist.

## <a name="syntax"></a>Syntax

```cpp
[oleautomation]
```

## <a name="remarks"></a>Bemerkungen

Das **oleautomation** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut [oleautomation](/windows/win32/Midl/oleautomation) .

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **oleautomation**finden Sie in den Beispielen für [DefaultValue](defaultvalue.md) und [nonextensible](nonextensible.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|**dispinterface**|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)
