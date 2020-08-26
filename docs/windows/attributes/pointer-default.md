---
title: Pointer_default (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: e4e5ce03e8c0e6ca19814f5d228305b0d97322f9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836191"
---
# <a name="pointer_default"></a>pointer_default

Gibt das Standard Zeiger Attribut für alle Zeiger an, ausgenommen Zeiger der obersten Ebene, die in Parameterlisten angezeigt werden.

## <a name="syntax"></a>Syntax

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parameter

*value*<br/>
Ein Wert, der den Zeigertyp beschreibt: " **ptr**", " **ref**" oder " **Unique**".

## <a name="remarks"></a>Bemerkungen

Das **Pointer_default** C++-Attribut verfügt über die gleiche Funktionalität wie das [Pointer_default](/windows/win32/Midl/pointer-default) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Pointer_default**finden Sie im Beispiel für [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)
