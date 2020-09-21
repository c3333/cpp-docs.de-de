---
title: Compilerfehler C3225
ms.date: 11/04/2016
f1_keywords:
- C3225
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
ms.openlocfilehash: ed645535300e0a7c4d27f8bed43d3143bae7e97a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742865"
---
# <a name="compiler-error-c3225"></a>Compilerfehler C3225

das generische Typargument für ' arg ' kann nicht ' type ' sein, es muss ein Werttyp oder ein behandlertyp sein.

Das generische Typargument war nicht vom richtigen Typ.

Weitere Informationen finden Sie unter [Generics](../../extensions/generics-cpp-component-extensions.md).

## <a name="examples"></a>Beispiele

Es ist nicht möglich, einen generischen Typ mit einem systemeigenen Typ zu instanziieren. Im folgenden Beispiel wird C3225 generiert.

```cpp
// C3225.cpp
// compile with: /clr
class A {};

ref class B {};

generic <class T>
ref class C {};

int main() {
   C<A>^ c = gcnew C<A>;   // C3225
   C<B^>^ c2 = gcnew C<B^>;   // OK
}
```

Im folgenden Beispiel wird eine Komponente mit c# erstellt. Beachten Sie, dass die-Einschränkung angibt, dass der generische Typ nur mit einem Werttyp instanziiert werden kann.

```
// C3225_b.cs
// compile with: /target:library
// a C# program
public class MyList<T> where T: struct {}
```

Dieses Beispiel verwendet die von c# erstellte Komponente und verstößt gegen die Einschränkung, dass myList nur mit einem anderen Werttyp als instanziiert werden kann <xref:System.Nullable> . Im folgenden Beispiel wird C3225 generiert.

```cpp
// C3225_c.cpp
// compile with: /clr
#using "C3225_b.dll"
ref class A {};
value class B {};
int main() {
   MyList<A> x;   // C3225
   MyList<B> y;   // OK
}
```
