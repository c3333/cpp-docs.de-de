---
title: Compilerwarnung (Stufe 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: df80bec2294929be463425d74d4bf00421b368e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198431"
---
# <a name="compiler-warning-level-4-c4235"></a>Compilerwarnung (Stufe 4) C4235

Nicht dem Standard entsprechende Erweiterung: Das Schlüsselwort 'Schlüsselwort' wird für diese Architektur nicht unterstützt

Das von Ihnen verwendete Schlüsselwort wird vom Compiler nicht unterstützt.

Diese Warnung wird automatisch zu einem Fehler heraufgestuft. Wenn Sie dieses Verhalten ändern möchten, verwenden Sie [#pragma Warnung](../../preprocessor/warning.md). Um C4235 beispielsweise in eine Warnung der Stufe 2 umzuwandeln, verwenden Sie folgende Codezeile

```cpp
#pragma warning(2:4235)
```

in der Quellcodedatei.
