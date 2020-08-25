---
title: Hidden (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: ffa1ce01cfd570de7b699e415f10b27acf525047
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830955"
---
# <a name="hidden"></a>hidden

Gibt an, dass das Element vorhanden ist, aber nicht in einem benutzerorientierten Browser angezeigt werden soll.

## <a name="syntax"></a>Syntax

```cpp
[hidden]
```

## <a name="remarks"></a>Bemerkungen

Das ausgeblendete C++-Attribut verfügt **über die gleiche** Funktionalität wie das [verborgene](/windows/win32/Midl/hidden) Mittel l-Attribut.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Hidden**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**Schnittstelle**, **`class`** , **`struct`** , Methode, Eigenschaft|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**Co-Klasse** (bei Anwendung auf **`class`** oder **`struct`** )|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)
