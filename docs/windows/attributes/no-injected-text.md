---
title: no_injected_text (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166613"
---
# <a name="no_injected_text"></a>no_injected_text

Verhindert, dass der Compiler Code als Ergebnis der Verwendung eines Attributs einfügt.

## <a name="syntax"></a>Syntax

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parameter

*boolean*<br/>
Optionale " **true** ", wenn kein Code eingefügt werden soll, " **false** ", um zuzulassen, dass Code eingefügt wird. der Standardwert ist " **true** ".

## <a name="remarks"></a>Bemerkungen

Die häufigste Verwendung des **no_injected_text** C++ -Attributs ist die [/FX](../../build/reference/fx-merge-injected-code.md) -Compileroption, die das **no_injected_text** -Attribut in die MRG-Datei einfügt.

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

[Compilerattribute](compiler-attributes.md)
