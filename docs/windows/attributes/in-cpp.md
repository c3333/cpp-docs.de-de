---
title: in (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: 2838a00ffe365f42fb7778b654306eb0c73b5996
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842233"
---
# <a name="in-c"></a>in (C++)

Gibt an, dass ein Parameter von der aufrufenden Prozedur an die aufgerufene Prozedur übergeben werden soll.

## <a name="syntax"></a>Syntax

```cpp
[in]
```

## <a name="remarks"></a>Bemerkungen

Das **in** C++-Attribut verfügt über die gleiche Funktionalität wie das [in](/windows/win32/Midl/in) -Attribut.

## <a name="example"></a>Beispiel

Unter [bindbare](bindable.md) finden Sie ein Beispiel für die Verwendung von **in**.

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|**retval**|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[DefaultValue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)
