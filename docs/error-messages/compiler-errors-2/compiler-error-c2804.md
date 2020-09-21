---
title: Compilerfehler C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: bdd1b4155d30dd2513d87ac217ca20ca7baabd8a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743164"
---
# <a name="compiler-error-c2804"></a>Compilerfehler C2804

Binärer Operator "Operator" hat zu viele Parameter

Die überladene binäre Operator-Memberfunktion wird mit mehr als einem Parameter deklariert. Der erste Parameter für Operanden einer binären Operator-Memberfunktion, deren Typ des Operators ist einschließender Typ ist, wird impliziert.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2804 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

Im folgenden Beispiel wird C2804 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```
