---
title: Compilerfehler C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: b033d95b127a45451a776cdc336ea7d2649d3716
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209746"
---
# <a name="compiler-error-c2217"></a>Compilerfehler C2217

"attribute1" erfordert "attribute2".

Das erste Funktions Attribut erfordert das zweite Attribut.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Interrupt ( `__interrupt` )-Funktion, die als deklariert wird `near` . Interrupt-Funktionen müssen sein `far` .

1. Die mit oder deklarierte Interruptfunktion **`__stdcall`** **`__fastcall`** . Interrupt-Funktionen müssen C-Aufruf Konventionen verwenden.

## <a name="example"></a>Beispiel

C2217 kann auch auftreten, wenn Sie versuchen, einen Delegaten an eine CLR-Funktion zu binden, die eine Variable Anzahl von Argumenten annimmt. Wenn die Funktion auch über eine e-param-Array Überladung verfügt, verwenden Sie diese stattdessen. Im folgenden Beispiel wird C2217 generiert.

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
