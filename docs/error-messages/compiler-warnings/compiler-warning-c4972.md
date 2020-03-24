---
title: Compilerwarnung C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: ca80e847174bbe225acaf8631c646d8c6a94c50a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164832"
---
# <a name="compiler-warning-c4972"></a>Compilerwarnung C4972

Das direkte Ändern oder Behandeln des Ergebnisses eines Unboxing-Vorgangs als L-Wert kann nicht überprüft werden.

Das Dereferenzieren eines Handles für einen Werttyp (auch als Unboxing bezeichnet) und das anschließende Zuweisen ist nicht überprüfbar.

Weitere Informationen finden Sie unter [Boxing](../../extensions/boxing-cpp-component-extensions.md)definiert sind.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4972 generiert.

```cpp
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```
