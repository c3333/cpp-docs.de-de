---
title: Compilerwarnung (Stufe 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: b62f382759c7e4c9dc888cf75d4df07a063df571
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199861"
---
# <a name="compiler-warning-level-1-c4215"></a>Compilerwarnung (Stufe 1) C4215

nicht dem Standard entsprechende Erweiterung: Long float

Die standardmäßigen Microsoft-Erweiterungen (/Ze) behandeln **Long float** als **Double**. Die ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ist nicht. Verwenden Sie **Double** , um die Kompatibilität aufrechtzuerhalten.

Im folgenden Beispiel wird C4215 generiert:

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```
