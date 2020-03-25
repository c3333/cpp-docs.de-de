---
title: propputref (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: a9c4413e9bb8c7faa332bb842700dfcf84d6666a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166431"
---
# <a name="propputref"></a>propputref

Gibt eine Eigenschafts Einstellungs Funktion an, die einen Verweis anstelle eines Werts verwendet.

## <a name="syntax"></a>Syntax

```cpp
[propputref]
```

## <a name="remarks"></a>Bemerkungen

Das **PROPPUTREF** C++ -Attribut verfügt über die gleiche Funktionalität wie das [PROPPUTREF](/windows/win32/Midl/propputref) -Attribut "mittlerl".

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **PROPPUTREF**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`propget`, `propput`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
