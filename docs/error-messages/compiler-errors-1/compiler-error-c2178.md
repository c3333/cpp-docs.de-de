---
title: Compilerfehler C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 4904c7009151748b4585060c816e0bd5c407be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225552"
---
# <a name="compiler-error-c2178"></a>Compilerfehler C2178

'*Identifier*' kann nicht mit dem Spezifizierer '*Spezifizierer*' deklariert werden.

Ein **`mutable`** Spezifizierer wurde in einer Deklaration verwendet, aber der Spezifizierer ist in diesem Kontext nicht zulässig.

Der **`mutable`** Spezifizierer kann nur auf Namen von klassendatenmembern angewendet werden und kann nicht auf Namen angewendet werden, die als **`const`** oder deklariert **`static`** sind, und kann nicht auf Verweismember angewendet werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie C2178 auftreten kann und wie es behoben werden kann.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
