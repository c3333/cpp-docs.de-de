---
title: cpp_quote (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 27be83d123b5433f79c4c8a702197fc6f9f1a753
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833165"
---
# <a name="cpp_quote"></a>cpp_quote

Gibt die angegebene Zeichenfolge ohne Anführungszeichen in der generierten IDL-Datei aus.

## <a name="syntax"></a>Syntax

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parameter

*statement*<br/>
Eine C-Anweisung.

## <a name="remarks"></a>Bemerkungen

Das **cpp_quote** C++-Attribut ist nützlich, wenn Sie eine Präprozessordirektive in eine IDL-Datei einfügen möchten.

Sie können auch **cpp_quote** verwenden und eine h-Datei als Teil der Mittell-Kompilierung generieren. Wenn Sie z. b. über eine C++-Header Datei verfügen, die C++ IDL-Attribute verwendet, diese Datei jedoch nicht für eine Aufgabe verwenden kann, können Sie Sie kompilieren, um eine von der Mitte generierte h-Datei zu erstellen, die Sie verwenden können.

Das **cpp_quote** -Attribut verfügt über die gleiche Funktionalität wie das [cpp_quote](/windows/win32/Midl/cpp-quote) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung **cpp_quote**finden Sie im Beispiel für [Dual](dual.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

| Attribut Kontext | Wert |
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)
