---
title: HelpFile (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 1f928fa281c99630ad52ce1fde184c44e9387263
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166977"
---
# <a name="helpfile"></a>helpfile

Legt den Namen der Hilfedatei für eine Typbibliothek fest.

## <a name="syntax"></a>Syntax

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parameter

*filename*<br/>
Der Name der Datei, die die Hilfe Themen enthält.

## <a name="remarks"></a>Bemerkungen

Das **HelpFile** C++ -Attribut verfügt über die gleiche Funktionalität wie das Mittel l-Attribut [HelpFile](/windows/win32/Midl/helpfile) .

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von **HelpFile**finden Sie im Beispiel für das [Modul](module-cpp.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Schnittstelle**, **typedef**, **Klasse**, Methode, **Eigenschaft**|
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
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
