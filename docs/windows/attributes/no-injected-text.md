---
title: no_injected_text (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 7e5c822c45888f41e8dd849f25658d0139e6fda0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201244"
---
# <a name="no_injected_text"></a>no_injected_text

Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.

## <a name="syntax"></a>Syntax

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parameter

*boolean*<br/>
(Optional) **`true`** Wenn kein Code eingefügt werden soll, kann der **`false`** Code eingefügt werden. **`true`** der Standardwert ist.

## <a name="remarks"></a>Bemerkungen

Die häufigste Verwendung des **no_injected_text** C++-Attributs ist die [/FX](../../build/reference/fx-merge-injected-code.md) -Compileroption, die das **no_injected_text** -Attribut in die MRG-Datei einfügt.

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Zielgruppe**|Überall|
|**REPEATABLE**|Nein|
|**Erforderliche Attribute**|Keine|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[Compilerattribute](compiler-attributes.md)
