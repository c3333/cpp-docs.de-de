---
title: Compilerwarnung (Stufe 4) C4932
description: Beschreibt die Microsoft C/C++-Compilerwarnung C4932.
ms.date: 08/25/2020
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: ece2ae14fd8e1198a97f5e772fcce52c47464878
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898299"
---
# <a name="compiler-warning-level-4-c4932"></a>Compilerwarnung (Stufe 4) C4932

> `__identifier(identifier_1)` und `__identifier(identifier_2)` sind nicht unterscheidbar.

Der Compiler kann nicht zwischen **`_finally`** und **`__finally`** oder **`__try`** und **`_try`** als Parameter unterscheiden, die an übergeben werden [`__identifier`](../../extensions/identifier-cpp-cli.md) . Sie sollten nicht beide Bezeichner im selben Programm verwenden, weil dadurch der Fehler [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) verursacht wird.

Im folgenden Beispiel wird C4932 generiert:

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
