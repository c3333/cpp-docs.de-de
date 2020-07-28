---
title: Compilerfehler C2254
ms.date: 11/04/2016
f1_keywords:
- C2254
helpviewer_keywords:
- C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
ms.openlocfilehash: 0be867d577b158ffc852ed7a751f99ded6e2482e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214697"
---
# <a name="compiler-error-c2254"></a>Compilerfehler C2254

"Function": ein reiner Spezifizierer oder ein abstrakter Überschreibungsspezifizierer ist für Friend-Funktion

Eine **`friend`** Funktion wird als rein angegeben **`virtual`** .

Im folgenden Beispiel wird C2254 generiert:

```cpp
// C2254.cpp
// compile with: /c
class A {
public:
   friend void func1() = 0;   // C2254, func1 is friend
   void virtual func2() = 0;   // OK, pure virtual
   friend void func3();   // OK, friend not virtual nor pure
};

void func1() {};
void func3() {};
```
