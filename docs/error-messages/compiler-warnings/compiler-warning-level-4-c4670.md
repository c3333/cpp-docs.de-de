---
title: Compilerwarnung (Stufe 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 15f0b249d9e91c0ebcc5655b5edffbd2d8cafa93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230609"
---
# <a name="compiler-warning-level-4-c4670"></a>Compilerwarnung (Stufe 4) C4670

'bezeichner': Auf diese Basisklasse kann nicht zugegriffen werden.

Auf die angegebene Basisklasse eines Objekts, das in einem-Block ausgelöst werden soll, kann nicht zugegriffen werden **`try`** . Das Objekt kann nicht instanziiert werden, wenn es ausgelöst wird. Überprüfen Sie, ob die Basisklasse mit dem richtigen Zugriffsspezifizierer geerbt wird.

Im folgenden Beispiel wird C4670 generiert.

```cpp
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```
