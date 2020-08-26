---
title: propput (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 11f216dd183f3977aee9af90c6579d01cad45fdf
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839945"
---
# <a name="propput"></a>propput

Gibt eine Eigenschaftseinstellungsfunktion an.

## <a name="syntax"></a>Syntax

```cpp
[propput]
```

## <a name="remarks"></a>Bemerkungen

Das Attribut " **PROPPUT** C++" verfügt über die gleiche Funktionalität wie das " [PROPPUT](/windows/win32/Midl/propput) "-Attribut "Mittel".

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **PROPPUT**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`propget`, `propputref`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
