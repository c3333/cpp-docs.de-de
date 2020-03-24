---
title: Compilerwarnung (Stufe 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 2521366a9f33e8c5b1b7d41951a7cb08adfc2561
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199822"
---
# <a name="compiler-warning-level-1-c4216"></a>Compilerwarnung (Stufe 1) C4216

nicht dem Standard entsprechende Erweiterung: float Long

Die standardmäßigen Microsoft-Erweiterungen (/Ze) behandeln **float Long** als **Double**. Die ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ist nicht. Verwenden Sie **Double** , um die Kompatibilität aufrechtzuerhalten. Im folgenden Beispiel wird C4216 generiert:

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```
