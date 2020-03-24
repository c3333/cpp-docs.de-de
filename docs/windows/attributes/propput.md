---
title: propput (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: 8817d0042c3055b5bbf9b111e6f02b9d9a4c152c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166444"
---
# <a name="propput"></a>propput

Gibt eine Eigenschaftseinstellungsfunktion an.

## <a name="syntax"></a>Syntax

```cpp
[propput]
```

## <a name="remarks"></a>Bemerkungen

Das **PROPPUT** C++ -Attribut verfügt über die gleiche Funktionalität wie das- [PROPPUT](/windows/win32/Midl/propput) -Attribut "Mittel l".

## <a name="example"></a>Beispiel

Eine Beispiel Verwendung von **PROPPUT**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`propget`, `propputref`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
