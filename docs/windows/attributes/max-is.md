---
title: Max_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: 2e30595a549eefc6a5eecc27be98ded5221dcc16
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201309"
---
# <a name="max_is"></a>max_is

Legt den maximalen Wert für einen gültigen Array Index fest.

## <a name="syntax"></a>Syntax

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Mindestens ein C-sprach Ausdruck. Leere Argument Slots sind zulässig.

## <a name="remarks"></a>Bemerkungen

Das **Max_is** C++-Attribut verfügt über die gleiche Funktionalität wie das [Max_is](/windows/win32/Midl/max-is) -Attribut "Mittel".

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|Feld in **`struct`** oder **`union`** , Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|**size_is**|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Beispiel

Ein Beispiel für die Angabe eines Abschnitts eines Arrays finden Sie unter [First_is](first-is.md) .

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
