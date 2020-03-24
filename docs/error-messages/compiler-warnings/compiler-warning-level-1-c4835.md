---
title: Compilerwarnung (Stufe 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: f86fcaea8a742c19ce175a453c06669178ed2145
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174855"
---
# <a name="compiler-warning-level-1-c4835"></a>Compilerwarnung (Stufe 1) C4835

' Variable ': der Initialisierer für exportierte Daten wird erst ausgeführt, wenn der verwaltete Code zuerst in der Hostassembly ausgeführt wird.

Wenn Sie auf Daten zwischen verwalteten Komponenten zugreifen, empfiehlt es sich, keine nativen C++ Import-und Export Mechanismen zu verwenden. Deklarieren Sie die Datenmember stattdessen in einem verwalteten Typ, und verweisen Sie mit `#using` im Client auf die Metadaten. Weitere Information finden Sie unter [#using Directive (#using-Direktive)](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4835 generiert.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die-Komponente verwendet, die im vorherigen Beispiel erstellt wurde, und es wird gezeigt, dass der Wert der Variablen nicht erwartungsgemäß ist.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
