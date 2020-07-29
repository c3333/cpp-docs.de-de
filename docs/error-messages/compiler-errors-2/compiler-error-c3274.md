---
title: Compilerfehler C3274
ms.date: 11/04/2016
f1_keywords:
- C3274
helpviewer_keywords:
- C3274
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
ms.openlocfilehash: c2c7de919181cd0e89526f8ffacabaec73fb8f89
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223433"
---
# <a name="compiler-error-c3274"></a>Compilerfehler C3274

'__finally/finally' ohne entsprechendes 'try'

Eine [__finally](../../cpp/try-finally-statement.md) -oder [schließlich](../../dotnet/finally.md) -Anweisung wurde ohne übereinstimmendes gefunden **`try`** . Um dieses Problem zu beheben, löschen Sie entweder die- **`__finally`** Anweisung, oder fügen Sie eine- **`try`** Anweisung für hinzu **`__finally`** .

Im folgenden Beispiel wird C3274 generiert:

```cpp
// C3274.cpp
// compile with: /clr
// C3274 expected
using namespace System;
int main() {
   try {
      try {
         throw gcnew ApplicationException();
      }
      catch(...) {
         Console::Error->WriteLine(L"Caught an exception");
      }
      finally {
         Console::WriteLine(L"In finally");
      }
   } finally {
      Console::WriteLine(L"In finally");
   }

   // Uncomment the following 3 lines to resolve.
   // try {
   //   throw gcnew ApplicationException();
   // }

   finally {
      Console::WriteLine(L"In finally");
   }
   Console::WriteLine(L"**FAIL**");
}
```
