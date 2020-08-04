---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7a1d9bd64a28fa7c08477c6011dc0e8236b7bcf6
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521251"
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

- **Gilt für**: nicht-com `interface` , `idl_module` Methoden, Schnittstellenmember, Schnittstellenparameter,,,,, **`typedef`** **`class`** **`enum`** **`union`** und **`struct`** .
- **Wiederholbar**: Ja.
- **Erforderliche Attribute**: **Co-Klasse** (bei Verwendung in der-Klasse).
- **Ungültige Attribute**: None.

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Siehe auch

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[Parameterattribute](parameter-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)
