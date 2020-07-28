---
title: Compilerwarnung (Stufe 4) C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 33a2a4e36a2c1d3a3900b9f2f8261df7bbce9b00
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214346"
---
# <a name="compiler-warning-level-4-c4487"></a>Compilerwarnung (Stufe 4) C4487

"derived_class_function": stimmt mit der geerbten nicht virtuellen Methode "base_class_function" überein, ist jedoch nicht explizit als "New" markiert.

Eine Funktion in einer abgeleiteten Klasse verfügt über dieselbe Signatur wie eine nicht virtuelle Basisklassen Funktion. C4487 erinnert Sie daran, dass die Funktion der abgeleiteten Klasse die Basisklassen Funktion nicht außer Kraft setzt. Markieren Sie die Funktion der abgeleiteten Klasse explizit als **`new`** , um diese Warnung zu beheben.

Weitere Informationen finden Sie unter [New (neuer Slot in Vtable)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4487 generiert.

```cpp
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```
