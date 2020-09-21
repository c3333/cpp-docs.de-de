---
title: Compilerfehler C2676
ms.date: 11/04/2016
f1_keywords:
- C2676
helpviewer_keywords:
- C2676
ms.assetid: 838a5e34-c92f-4f65-a597-e150bf8cf737
ms.openlocfilehash: 94e56581f6583fa69e46d4deb3d82663a65cd1d1
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743190"
---
# <a name="compiler-error-c2676"></a>Compilerfehler C2676

Binärer 'Operator': 'Typ' definiert diesen Operator oder eine Konvertierung in einen für den vordefinierten Operator geeigneten Typ nicht

Um den Operator zu verwenden, müssen Sie ihn für den angegebenen Typ überladen oder eine Konvertierung in einen Typ definieren, für den der Operator definiert ist.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2676 generiert.

```cpp
// C2676.cpp
// C2676 expected
struct C {
   C();
} c;

struct D {
   D();
   D operator >>( C& ){return * new D;}
   D operator <<( C& ){return * new D;}
} d;

struct E {
   // operator int();
};

int main() {
   d >> c;
   d << c;
   E e1, e2;
   e1 == e2;   // uncomment operator int in class E, then
               // it is OK even though neither E::operator==(E) nor
               // operator==(E, E) defined. Uses the conversion to int
               // and then the builtin-operator==(int, int)
}
```

C2676 kann auch auftreten, wenn Sie versuchen, eine Zeigerarithmetik für den **`this`** Zeiger eines Verweis Typs durchzuführen.

Der **`this`** Zeiger ist vom Typ Handle in einem Verweistyp. Weitere Informationen finden Sie unter [Semantik des this-Zeigers](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

Im folgenden Beispiel wird C2676 generiert.

```cpp
// C2676_a.cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      Console::WriteLine("{0}", this + 3.3);   // C2676
      Console::WriteLine("{0}", this[3.3]);   // OK
   }
};

int main() {
   A ^ mya = gcnew A();
}
```
