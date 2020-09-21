---
title: Compilerfehler C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 59d0e5d5a5f0957f2d73cdb863ccee9a2dd2a026
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743255"
---
# <a name="compiler-error-c2027"></a>Compilerfehler C2027

Verwendung des nicht definierten Typs "Typ"

Ein Typ kann erst verwendet werden, nachdem er definiert wurde. Um den Fehler zu beheben, stellen Sie sicher, dass der Typ vollständig definiert ist, bevor Sie darauf verweisen.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2027 generiert.

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

Es ist möglich, einen Zeiger auf einen deklarierten, aber nicht definierten Typ zu deklarieren. C++ lässt jedoch keinen Verweis auf einen nicht definierten Typ zu.

Im folgenden Beispiel wird C2027 generiert.

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
