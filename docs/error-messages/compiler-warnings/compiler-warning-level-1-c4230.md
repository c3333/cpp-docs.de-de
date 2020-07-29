---
title: Compilerwarnung (Stufe 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: 0b590eaef2094c3d1c3a83541e9d5e10415928f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223212"
---
# <a name="compiler-warning-level-1-c4230"></a>Compilerwarnung (Stufe 1) C4230

Anachronismus verwendet: Modifizierer/Qualifizierer (interspersed); Qualifizierer ignoriert

Die Verwendung eines Qualifizierers vor einem Microsoft-Modifizierer, z **`__cdecl`** . b., ist eine veraltete

## <a name="example"></a>Beispiel

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
