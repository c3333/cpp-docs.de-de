---
title: Compilerwarnung (Stufe 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 11a1bcdc8396b1eb74121c27154b8c6c24fa92a6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162282"
---
# <a name="compiler-warning-level-1-c4561"></a>Compilerwarnung (Stufe 1) C4561

' __fastcall ' ist nicht kompatibel mit der Option '/CLR ': die Umstellung auf '\__stdcall '

Die [__fastcall](../../cpp/fastcall.md) -Funktionsaufruf Konvention kann nicht mit der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Compileroption verwendet werden. Der Compiler ignoriert die Aufrufe an `__fastcall`. Um diese Warnung zu beheben, entfernen Sie entweder die Aufrufe von **__fastcall** oder Kompilieren ohne **/CLR**.

Im folgenden Beispiel wird C4561 generiert:

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
