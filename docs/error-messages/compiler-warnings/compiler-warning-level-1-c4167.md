---
title: Compilerwarnung (Stufe 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 99d60bc08a077ae1637b80eac6775c8fa2571a1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163597"
---
# <a name="compiler-warning-level-1-c4167"></a>Compilerwarnung (Stufe 1) C4167

Funktion: Nur als systeminterne Funktion verfügbar

Die **#pragma-Funktion** versucht zu erzwingen, dass der Compiler einen konventionellen Aufruf für eine Funktion verwendet, die in systeminterner Form verwendet werden muss. Das Pragma wird ignoriert.

Um diese Warnung zu vermeiden, entfernen Sie die **#pragma-Funhtion**.

## <a name="example"></a>Beispiel

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```
