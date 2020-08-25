---
title: local (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: dea62653478e451af00fa47b72984f3b580aadc0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834088"
---
# <a name="local-c"></a>local (C++)

Wenn Sie im Schnittstellen Header verwendet wird, können Sie den Mittel l-Compiler als Header Generator verwenden. Gibt bei Verwendung in einer einzelnen Funktion eine lokale Prozedur an, für die keine stubals generiert werden.

## <a name="syntax"></a>Syntax

```cpp
[local]
```

## <a name="remarks"></a>Bemerkungen

Das **lokale** C++-Attribut verfügt über die gleiche Funktionalität wie das [lokale](/windows/win32/Midl/local) -Attribut.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **local**finden Sie unter [Call_as](call-as.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**Schnittstelle**, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`dispinterface`|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[call_as](call-as.md)
