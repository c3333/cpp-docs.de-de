---
title: Compilerfehler C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 2697ce5a790fffe762d97ca3380853514de6d437
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220261"
---
# <a name="compiler-error-c2682"></a>Compilerfehler C2682

Casting_operator kann nicht zum Konvertieren von "Typ1" in "Typ2" verwendet werden.

Ein Umwandlungs Operator hat versucht, zwischen nicht kompatiblen Typen zu konvertieren. Beispielsweise können Sie den [dynamic_cast](../../cpp/dynamic-cast-operator.md) -Operator nicht verwenden, um einen Zeiger auf einen Verweis zu konvertieren. Der **`dynamic_cast`** Operator kann nicht zum Umwandeln von Qualifizierern verwendet werden. Alle Qualifizierer für die Typen müssen mit identisch sein.

Sie können den- **`const_cast`** Operator verwenden, um Attribute wie **`const`** , **`volatile`** oder zu entfernen **`__unaligned`** .

Im folgenden Beispiel wird C2682 generiert:

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

Im folgenden Beispiel wird C2682 generiert:

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
