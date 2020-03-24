---
title: HelpContext (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 292db21e8092284a92b09ef3f889bb0475d0d886
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167003"
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

Das **HelpContext** C++ -Attribut verfügt über die gleiche Funktionalität wie das " [HelpContext](/windows/win32/Midl/helpcontext) "-Attribut "Mittel l".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **HelpContext**finden Sie im Beispiel für [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Schnittstelle**, **typedef**, **Klasse**, Methode, Eigenschaft|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Schnittstellenattribut](interface-attributes.md)<br/>
[Klassenattribute](class-attributes.md)<br/>
[Methodenattribut](method-attributes.md)<br/>
[typedef-, enum-, union- und struct-Attribute](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
