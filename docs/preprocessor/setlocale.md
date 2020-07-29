---
title: setlocale-Pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 9603c132610e0cfb1e8f955be48271870527105b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219377"
---
# <a name="setlocale-pragma"></a>setlocale-Pragma

Definiert das Gebiets Schema, das Land, die Region *und die Sprache*, die beim Übersetzen von breit Zeichen Konstanten und Zeichenfolgenliteralen verwendet werden.

## <a name="syntax"></a>Syntax

> **#pragma setlocale ("** [ *locale-String* ] **")**

## <a name="remarks"></a>Bemerkungen

Da der Algorithmus zum Umrechnen von Multibytezeichen in breit Zeichen je nach Gebiets Schema variieren kann, oder die Kompilierung in einem anderen Gebiets Schema stattfinden kann, in dem eine ausführbare Datei ausgeführt wird, bietet dieses Pragma eine Möglichkeit, das Ziel Gebiets Schema zur Kompilierzeit anzugeben. Sie gewährleistet, dass breit Zeichen-Zeichen folgen im richtigen Format gespeichert werden.

Die standardmäßige Gebiets Schema *Zeichenfolge* ist "".

Das Gebiets Schema "C" ordnet jedes Zeichen in der Zeichenfolge dem Wert als zu **`wchar_t`** . Weitere gültige Werte für `setlocale` sind die Einträge, die in der Liste der [Sprachen](../c-runtime-library/language-strings.md) Zeichenfolgen gefunden werden. Beispielsweise können Sie Folgendes angeben:

```cpp
#pragma setlocale("dutch")
```

Die Möglichkeit, eine Sprachen Zeichenfolge anzugeben, hängt von der Codepage und der Sprach-ID auf dem Computer ab.

## <a name="see-also"></a>Weitere Informationen

[Pragma-Anweisungen und das __pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
