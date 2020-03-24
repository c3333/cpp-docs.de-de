---
title: cpp_quote (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 451313b5bd1eb5011f1175de5c3bcfe6fb054299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214915"
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

Das **cpp_quote** C++ -Attribut ist nützlich, wenn Sie eine Präprozessordirektive in eine IDL-Datei einfügen möchten.

Sie können auch **cpp_quote** verwenden und eine h-Datei als Teil der Mittell-Kompilierung generieren. Wenn Sie z. b. über C++ eine Header Datei verfügen C++ , die IDL-Attribute verwendet, diese Datei jedoch nicht für eine Aufgabe verwenden kann, können Sie Sie kompilieren, um eine von der Mittel l generierte h-Datei zu erstellen, die Sie verwenden können.

Das **cpp_quote** -Attribut verfügt über die gleiche Funktionalität wie das [cpp_quote](/windows/win32/Midl/cpp-quote) -Attribut "Mittel".

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung **cpp_quote**finden Sie im Beispiel für [Dual](dual.md) .

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Überall|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[IDL-Attribute](idl-attributes.md)<br/>
[Eigenständige Attribute](stand-alone-attributes.md)
