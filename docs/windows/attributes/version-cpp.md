---
title: Version (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: b537f56c39c33abc52897cf53ea2cc0fb24ee458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213800"
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

Das **Version** C++-Attribut verfügt über die gleiche Funktionalität wie das-Attribut der runl- [Version](/windows/win32/Midl/version) und wird an die generierte IDL-Datei übermittelt.

## <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung der- **Version**finden Sie im [bindbare](bindable.md) -Beispiel.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|**`class`**, **`struct`**|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|**coclass**|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)<br/>
[Klassenattribute](class-attributes.md)
