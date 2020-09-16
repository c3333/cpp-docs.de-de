---
title: Compilerfehler C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 97d6dc0544176d90b90702a7d1f1648e8e98d756
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686625"
---
# <a name="compiler-error-c3821"></a>Compilerfehler C3821

"Funktion": ein verwalteter Typ oder eine verwaltete Funktion kann nicht in einer nicht verwalteten Funktion verwendet werden.

Funktionen mit der Inlineassembly oder [setjmp](../../c-runtime-library/reference/setjmp.md) können keine Werttypen oder verwalteten Klassen enthalten. Entfernen Sie die Inlineassembly, `setjmp` oder entfernen Sie die verwalteten Objekte, um diesen Fehler zu beheben.

C3821 kann auch auftreten, wenn Sie versuchen, den automatischen Speicher in einer vararg-Funktion zu verwenden.  Weitere Informationen finden Sie unter [Variablen Argument Listen (...) (C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) und [C++ Stack-Semantik für Verweis Typen](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3821 generiert.

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

Im folgenden Beispiel wird C3821 generiert.

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
