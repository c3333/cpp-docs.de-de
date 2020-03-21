---
title: Compilerfehler C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: d4a69d7dffb4a01a91b14c3858cb0a5d553d1cf8
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075166"
---
# <a name="compiler-error-c3767"></a>Compilerfehler C3767

'Funktion': Auf mögliche Funktion(en) kann nicht zugegriffen werden

Bei einer in einer Klasse definierten Friend-Funktion wird nicht davon ausgegangen, dass sie so behandelt wird, als wäre sie im globalen Gültigkeitsbereich des Namespaces definiert und deklariert worden. Sie kann jedoch mittels einer argumentbezogenen Suche gefunden werden.

C3767 kann auch durch ein Breaking Change verursacht werden: Native Typen sind jetzt standardmäßig in einer **/CLR** -Kompilierung privat. Weitere Informationen finden Sie unter [Typsichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3767 generiert:

```cpp
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

Im folgenden Beispiel wird C3767 generiert:

```cpp
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```
