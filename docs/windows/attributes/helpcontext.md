---
title: HelpContext (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 60e6bf66e088872a357751e4a7b7e043cd9b4dfc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845249"
---
# <a name="helpcontext"></a>helpcontext

Gibt eine Kontext-ID an, mit der der Benutzerinformationen zu diesem Element in der **Hilfe** Datei anzeigen kann.

## <a name="syntax"></a>Syntax

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parameter

*id*<br/>
Die Kontext-ID des Hilfe Themas. Weitere Informationen zu Kontext-IDs finden [Sie in der HTML-Hilfe: kontextbezogene Hilfe für Ihre Programme](../../mfc/html-help-context-sensitive-help-for-your-programs.md) .

## <a name="remarks"></a>Bemerkungen

Das **HelpContext** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut [HelpContext](/windows/win32/Midl/helpcontext) .

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **HelpContext**finden Sie im Beispiel für [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|**Schnittstelle**, **`typedef`** , **`class`** , Methode, Eigenschaft|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellen Attribute](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methoden Attribute](method-attributes.md)<br/>
[Typedef-, Aufzählungs-, Union-und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
