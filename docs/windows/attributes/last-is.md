---
title: Last_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 62377415dc0809033fcdcb8bd4e7997f667c1691
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214811"
---
# <a name="last_is"></a>last_is

Gibt den Index des letzten Array Elements an, das übertragen werden soll.

## <a name="syntax"></a>Syntax

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Mindestens ein C-sprach Ausdruck. Leere Argument Slots sind zulässig.

## <a name="remarks"></a>Bemerkungen

Das **Last_is** C++ -Attribut verfügt über die gleiche Funktionalität wie das [Last_is](/windows/win32/Midl/last-is) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Angabe eines Abschnitts eines Arrays finden Sie unter [First_is](first-is.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Feld in **Struktur** oder **Union**, Schnittstellenparameter, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
