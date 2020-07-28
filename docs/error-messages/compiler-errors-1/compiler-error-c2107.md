---
title: Compilerfehler C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 1be2ebb82aca481df9efbbc4ccdd54466ae60a3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214788"
---
# <a name="compiler-error-c2107"></a>Compilerfehler C2107

Ungültiger Index, Dereferenzierung nicht erlaubt

Die Indexschreibweise wurde für einen Ausdruck verwendet, dessen Ergebnis kein Zeiger ist.

## <a name="example"></a>Beispiel

C2107 kann auftreten, wenn Sie fälschlicherweise den **`this`** Zeiger eines Werttyps verwenden, um auf den Standardindexer des Typs zuzugreifen. Weitere Informationen finden Sie unter [Semantik des this-Zeigers](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Im folgenden Beispiel wird C2107 generiert.

```cpp
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
