---
title: Compilerwarnung (Stufe 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: df19f90e17d6737a2639eb1245da197881e35c96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218103"
---
# <a name="compiler-warning-level-4-c4211"></a>Compilerwarnung (Stufe 4) C4211

nicht dem Standard entsprechende Erweiterung: Neudefinition von extern in static

Mit den standardmäßigen Microsoft-Erweiterungen (/Ze) können Sie einen **`extern`** Bezeichner als neu definieren **`static`** .

## <a name="example"></a>Beispiel

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Diese Neudefinitionen sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
