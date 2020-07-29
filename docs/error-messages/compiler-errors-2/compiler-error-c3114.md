---
title: Compilerfehler C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 481e0ac5a395b38bc9d1874959b010ecd71f9fb5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233378"
---
# <a name="compiler-error-c3114"></a>Compilerfehler C3114

' Argument ': kein gültiges benanntes Attribut Argument.

Damit ein attributklassendatenmember ein gültiges benanntes Argument sein kann, darf er nicht als **`static`** , oder markiert werden **`const`** **`literal`** . Wenn eine Eigenschaft ist, darf die Eigenschaft nicht sein **`static`** und muss über Get-und Set-Accessoren verfügen.

Weitere Informationen finden Sie unter [Eigenschaft](../../extensions/property-cpp-component-extensions.md) und [benutzerdefinierte Attribute](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3114 generiert.

```cpp
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```
