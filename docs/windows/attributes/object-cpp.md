---
title: Object (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 4545d899c13a1eabf8ea5fb6fe3918fb5f05b626
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214669"
---
# <a name="object-c"></a>object (C++)

Identifiziert eine benutzerdefinierte-Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
[object]
```

## <a name="remarks"></a>Bemerkungen

Wenn eine Schnittstellen Definition vorangestellt wird, bewirkt das **Objekt** C++ Attribut, dass die-Schnittstelle in der IDL-Datei als benutzerdefinierte-Schnittstelle platziert wird.

Jede mit dem-Objekt markierte Schnittstelle muss von `IUnknown`erben. Diese Bedingung ist erfüllt, wenn eine der Basis Schnittstellen von `IUnknown`erbt. Wenn keine Basis Schnittstellen von `IUnknown`erben, bewirkt der Compiler, dass die mit **Object** markierte Schnittstelle von `IUnknown`abgeleitet wird.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **Object**finden Sie unter [nicht](nonbrowsable.md) suchbar.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**interface**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
