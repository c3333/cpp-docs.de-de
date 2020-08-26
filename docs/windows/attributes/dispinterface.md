---
title: dispinterface (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: dd2a0883418ff79af53285d3cf51dba7601a363c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845392"
---
# <a name="dispinterface"></a>dispinterface

Fügt eine Schnittstelle in die IDL-Datei als Verteilschnittstelle ein.

## <a name="syntax"></a>Syntax

```cpp
[dispinterface]
```

## <a name="remarks"></a>Bemerkungen

Wenn das C++-Attribut **dispinterface** einer Schnittstelle vorangeht, wird die Schnittstelle dadurch in den Bibliotheksblock in der generierten IDL-Datei eingefügt.

Solange Sie keine Basisklasse festlegen, wird eine Verteilschnittstelle von `IDispatch`abgeleitet. Sie müssen eine [ID](id.md) für die Member einer Verteilschnittstelle angeben.

Das Beispiel für die Verwendung von [dispinterface](/windows/win32/Midl/dispinterface) in der MIDL-Dokumentation:

```cpp
dispinterface helloPro
   { interface hello; };
```

ist nicht gültig für das Attribut **dispinterface** .

## <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel für [bindable](bindable.md) für ein Beispiel für die Verwendung von **dispinterface**an.

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**interface**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Attribute nach Verwendung](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[Zollunion](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
