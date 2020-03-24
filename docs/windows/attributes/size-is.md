---
title: size_is (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: c511901b3da03d14b1a09e178b70e8f78cd00f8c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166249"
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

Das **size_is** C++ -Attribut verfügt über die gleiche Funktionalität wie das [size_is](/windows/win32/Midl/size-is) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Angabe eines Abschnitts eines Arrays finden Sie im Beispiel für [First_is](first-is.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Feld in **Struktur** oder **Union**, Schnittstellenparameter, Schnittstellen Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`max_is`|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)
