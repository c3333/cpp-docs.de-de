---
title: Compilerwarnung (Stufe 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: fe8ae1f8ef8180f2d3c5ba9ae2401b9447b22527
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230635"
---
# <a name="compiler-warning-level-1-c4561"></a>Compilerwarnung (Stufe 1) C4561

' __fastcall ' ist nicht kompatibel mit der Option '/CLR ': wird in ' \_ _stdcall ' umgerechnet.

Die [__fastcall](../../cpp/fastcall.md) -Funktionsaufruf Konvention kann nicht mit der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Compileroption verwendet werden. Der Compiler ignoriert die Aufrufe von **`__fastcall`** . Um diese Warnung zu beheben, entfernen Sie entweder die Aufrufe von, **`__fastcall`** oder kompilieren Sie ohne **/CLR**.

Im folgenden Beispiel wird C4561 generiert:

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
