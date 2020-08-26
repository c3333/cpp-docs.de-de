---
title: Object (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: c0c0ff552d8a33ebe70f56b9b186e963cc8e9b3d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843104"
---
# <a name="object-c"></a>object (C++)

Identifiziert eine benutzerdefinierte-Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
[object]
```

## <a name="remarks"></a>Bemerkungen

Wenn eine Schnittstellen Definition vorangestellt wird, bewirkt das **Object** C++-Attribut, dass die-Schnittstelle in der IDL-Datei als benutzerdefinierte-Schnittstelle platziert wird.

Jede mit dem-Objekt markierte Schnittstelle muss von Erben `IUnknown` . Diese Bedingung ist erfüllt, wenn eine der Basis Schnittstellen von erbt `IUnknown` . Wenn keine Basis Schnittstellen von Erben `IUnknown` , bewirkt der Compiler, dass die mit **Object** markierte Schnittstelle von abgeleitet wird `IUnknown` .

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Object**finden Sie unter [nicht](nonbrowsable.md) suchbar.

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[Zollunion](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
