---
title: Compilerwarnung (Stufe 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173906"
---
# <a name="compiler-warning-level-4-c4234"></a>Compilerwarnung (Stufe 4) C4234

nicht dem Standard entsprechende Erweiterung: Schlüsselwort Schlüsselwort für zukünftige Verwendung reserviert

Der Compiler implementiert noch nicht das Schlüsselwort, das Sie verwendet haben.

Diese Warnung wird automatisch zu einem Fehler heraufgestuft. Wenn Sie dieses Verhalten ändern möchten, verwenden Sie [#pragma Warnung](../../preprocessor/warning.md). Wenn Sie z. b. C4234 zu einem Warnungs Problem auf der Ebene 4 machen möchten,

```cpp
#pragma warning(2:4234)
```

in der Quellcodedatei.
