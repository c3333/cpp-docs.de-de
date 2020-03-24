---
title: Compilerfehler C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201564"
---
# <a name="compiler-error-c2975"></a>Compilerfehler C2975

> '*Argument*': Ungültiges Vorlagen Argument für '*Type*', erwarteter Kompilierzeit-Konstantenausdruck.

Das Vorlagen Argument stimmt nicht mit der Vorlagen Deklaration identisch. ein konstanter Ausdruck sollte innerhalb der spitzen Klammern angezeigt werden. Variablen sind nicht als tatsächliche Vorlagen Argumente zulässig. Überprüfen Sie die Vorlagendefinition, um die richtigen Typen zu ermitteln.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2975 generiert und außerdem die korrekte Verwendung veranschaulicht:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 tritt auch auf, wenn &#95; &#95;Sie&#95; &#95; Line als Kompilierzeit Konstante mit [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)verwenden. Eine Lösung wäre die Kompilierung mit [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) anstelle von **/Zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```
