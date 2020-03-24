---
title: ID (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 79e49b2c074cd82323c74489e33812c10c442c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168056"
---
# <a name="id"></a>id

Gibt einen *DISPID-* Parameter für eine Element Funktion an (entweder eine Eigenschaft oder eine Methode in einer Schnittstelle oder einer dispinterface).

## <a name="syntax"></a>Syntax

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID für die Schnittstellen Methode.

## <a name="remarks"></a>Bemerkungen

Das **ID** C++ -Attribut verfügt über die gleiche Funktionalität wie das Attribut der [ID](/windows/win32/Midl/id) -Mittell.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung der **ID**finden Sie im Beispiel für [bindbare](bindable.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Schnittstellenmethode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[Datenmemberattribute](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)
