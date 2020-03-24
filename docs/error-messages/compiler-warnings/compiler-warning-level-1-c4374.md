---
title: Compilerwarnung (Stufe 1) C4374
ms.date: 11/04/2016
f1_keywords:
- C4374
helpviewer_keywords:
- C4374
ms.assetid: 4ac9aaec-d815-4b6e-825f-fa872092dd3b
ms.openlocfilehash: a0dbfbe931ec30c0bde2e82718e0817dcfa243b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187036"
---
# <a name="compiler-warning-level-1-c4374"></a>Compilerwarnung (Stufe 1) C4374

"Funktion1": die Schnittstellen Methode wird nicht von der nicht virtuellen Methode "Funktion2" implementiert.

Der Compiler hat erwartet, das [virtuelle](../../cpp/virtual-specifier.md) Schlüsselwort in einer Methoden Definition zu finden.

Im folgenden Beispiel wird C4374 generiert:

```cpp
// C4374.cpp
// compile with: /clr /W1 /c /WX
public interface class I {
   void f();
};

public ref struct B {
   void f() {
      System::Console::WriteLine("B::f()");
   }
};

public ref struct C {
   virtual void f() {
      System::Console::WriteLine("C::f()");
   }
};

public ref struct D : B, I {};   // C4374
public ref struct E : C, I {};   // OK
```
