---
title: Compilerfehler C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 8db79bf9813d9701b45d9a0427f68cfbecc3eba4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214671"
---
# <a name="compiler-error-c2462"></a>Compilerfehler C2462

' Identifier ': ein Typ kann nicht in ' New-Expression ' definiert werden.

Sie können im Operand-Feld des Operators keinen Typ definieren **`new`** . Legen Sie die Typdefinition in einer separaten Anweisung ab.

Im folgenden Beispiel wird C2462 generiert:

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
