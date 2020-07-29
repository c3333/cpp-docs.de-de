---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 185517720af7e61f6a04068e8868d258a51f262f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215321"
---
# <a name="custom-c"></a>custom (C++)

Definiert Metadaten für ein Objekt in der Typbibliothek.

## <a name="syntax"></a>Syntax

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Parameter

*uuid*<br/>
Eine eindeutige ID.

*value*<br/>
Ein Wert, der in eine Variante eingefügt werden kann.

## <a name="remarks"></a>Bemerkungen

Das **benutzerdefinierte** C++-Attribut bewirkt, dass Informationen in die Typbibliothek eingefügt werden. Sie benötigen ein Tool, das den benutzerdefinierten Wert aus der Typbibliothek liest.

Das **benutzerdefinierte** Attribut verfügt über die gleiche Funktionalität wie das [benutzerdefinierte](/windows/win32/Midl/custom) Attribut "Mittel l".

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|Nicht-com- **Schnittstelle**, **`class`** , **`enum`** s, `idl_module` Methoden, Schnittstellenmember, Schnittstellenparameter, s **`typedef`** **`union`** , **`struct`** s, s|
|**REPEATABLE**|Ja|
|**Erforderliche Attribute**|**Co-Klasse** (bei Verwendung für die Klasse)|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)
