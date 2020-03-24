---
title: Compilerwarnung (Stufe 1) C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 7852340bc056e126238a2d9c7493887ef3caf93e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174491"
---
# <a name="compiler-warning-level-1-c4964"></a>Compilerwarnung (Stufe 1) C4964

Es wurden keine Optimierungs Optionen angegeben. Profilinformationen werden nicht erfasst.

[/GL](../../build/reference/gl-whole-program-optimization.md) und [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) wurden angegeben, aber es wurden keine Optimierungen angefordert, sodass keine PGC-Dateien generiert werden und daher keine Profil gesteuerten Optimierungen möglich sind.

Wenn Sie möchten, dass PGC-Dateien generiert werden, wenn Sie die Anwendung ausführen, geben Sie eine der [/O](../../build/reference/o-options-optimize-code.md) -Compileroptionen an.

Im folgenden Beispiel wird C4964 generiert:

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```
