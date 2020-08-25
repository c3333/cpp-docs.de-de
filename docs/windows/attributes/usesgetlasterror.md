---
title: "\"US-GetLastError\" (C++ com-Attribut)"
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: e3d3c292554350d85296971a9bd3620909ef47c7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831631"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Teilt dem Aufrufer mit, dass der Aufrufer dann aufrufen kann, `GetLastError` um den Fehlercode abzurufen, wenn beim Aufrufen der Funktion ein Fehler auftritt.

## <a name="syntax"></a>Syntax

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Bemerkungen

Das Attribut **"C++" des** Attributs "" verfügt über die gleiche Funktionalität [wie das Attribut](/windows/win32/Midl/usesgetlasterror) "" für das Attribut "" in "".

## <a name="example"></a>Beispiel

Im [idl_module](idl-module.md) Beispiel wird ein Beispiel für **die Verwendung von**"" verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**Module** -Attribut|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)
