---
title: Entry (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 63e5ccebb1d3844af8dd11b4b094abe96e3e257c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845314"
---
# <a name="entry"></a>entry

Gibt eine exportierte Funktion oder Konstante in einem Modul an, indem der Einstiegspunkt in der DLL identifiziert wird.

## <a name="syntax"></a>Syntax

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Parameter

*id*<br/>
Die ID des Einstiegs Punkts.

## <a name="remarks"></a>Bemerkungen

Das C++-Attribut für den **Eintrag** verfügt über die gleiche Funktionalität wie das Attribut ["Mittel l](/windows/win32/Midl/entry) ".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Entry**finden Sie im Beispiel für [idl_module](idl-module.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|`idl_module`-Attribut|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)
