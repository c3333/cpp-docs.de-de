---
title: Compilerwarnung (Stufe 1) C4927
ms.date: 11/04/2016
f1_keywords:
- C4927
helpviewer_keywords:
- C4927
ms.assetid: 7009e740-a2ef-4130-96ba-482e092f717a
ms.openlocfilehash: 7f529435b3d95a64e53985d0fba96917d541e5fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174608"
---
# <a name="compiler-warning-level-1-c4927"></a>Compilerwarnung (Stufe 1) C4927

Ungültige Konvertierung; Es wurden mehrere benutzerdefinierte Konvertierungen implizit angewendet.

Mehr als eine benutzerdefinierte Konvertierung wird implizit auf einen einzelnen Wert angewendet, und der Compiler hat keine explizite Konvertierung gefunden, aber es wurde eine Konvertierung gefunden, die er verwendet hat.

Im folgenden Beispiel wird C4927 generiert:

```cpp
// C4927.cpp
// compile with: /W1
struct B
{
   operator int ()
   {
      return 0;
   }
};

struct A
{
   A(int i)
   {
   }

   /*
   // uncomment this constructor to resolve
   A(B b)
   {
   }
   */
};

A f1( B& b)
{
   return A(b);
}

B& f2( B& b)
{
   return b;
}

A f()
{
   B b;
   return A(b);   // ok
   return f1(b);  // ok
   return b;      // C4927
   return B(b);   // C4927
   return f2(b);  // C4927
}

int main()
{
   B b;
   A a = b;
   A a2(b);
}
```
