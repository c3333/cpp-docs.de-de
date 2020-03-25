---
title: Version (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: e5fcf80ef753a869b8798d6ab9c8e9f8ecff16fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165989"
---
# <a name="version-c"></a>version (C++)

Identifiziert eine bestimmte Version in mehreren Versionen einer Klasse.

## <a name="syntax"></a>Syntax

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parameter

*version*<br/>
Die Versionsnummer des `coclass`. Wenn nichts angegeben wird, wird 1,0 in die IDL-Datei eingefügt.

## <a name="remarks"></a>Bemerkungen

Das **Versions** C++ Attribut verfügt über die gleiche Funktionalität wie das runl-Attribut der [Version](/windows/win32/Midl/version) und wird an die generierte IDL-Datei übermittelt.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung der- **Version**finden Sie im [bindbare](bindable.md) -Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|**Klasse**, **Struktur**|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
