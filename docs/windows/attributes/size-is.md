---
title: size_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: dd0ec8622dfffdf9a0578c86d75d313042cc3c01
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841765"
---
# <a name="size_is"></a>size_is

Geben Sie die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger, große Zeiger auf Größen Zeiger und einzelne oder mehrdimensionale Arrays an.

## <a name="syntax"></a>Syntax

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Die Größe des zugeordneten Arbeitsspeichers für Größen Zeiger.

## <a name="remarks"></a>Bemerkungen

Das **size_is** C++-Attribut verfügt über die gleiche Funktionalität wie das [size_is](/windows/win32/Midl/size-is) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Angabe eines Abschnitts eines Arrays finden Sie im Beispiel für [First_is](first-is.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Feld in **`struct`** oder **`union`** , Schnittstellenparameter, Schnittstellen Methode|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`max_is`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)
