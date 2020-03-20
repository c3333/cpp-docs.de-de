---
title: 'Gewusst wie: Definieren eines statischen Schnittstellenkonstruktors (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 562605a579ac372e4a69953853a6e32668357565
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544970"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Gewusst wie: Definieren eines statischen Schnittstellenkonstruktors (C++/CLI)

Eine Schnittstelle kann über einen statischen Konstruktor verfügen, der zum Initialisieren statischer Datenmember verwendet werden kann.  Ein statischer Konstruktor wird höchstens einmal aufgerufen und vor dem ersten Zugriff auf einen statischen Schnittstellenmember aufgerufen.

## <a name="example"></a>Beispiel

```cpp
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Siehe auch

[Schnittstellenklasse](../extensions/interface-class-cpp-component-extensions.md)
