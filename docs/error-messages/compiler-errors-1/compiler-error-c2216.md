---
title: Compilerfehler C2216
ms.date: 11/04/2016
f1_keywords:
- C2216
helpviewer_keywords:
- C2216
ms.assetid: 250f6bdc-a5e1-495f-a1e8-6e8e7021ad9d
ms.openlocfilehash: 7da1816fbd8196501b043f09c6bf7da201b3de18
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742644"
---
# <a name="compiler-error-c2216"></a>Compilerfehler C2216

'Schlüsselwort1' kann nicht mit 'Schlüsselwort2' verwendet werden.

Zwei Schlüsselwörter, die sich gegenseitig ausschließen, wurden zusammen verwendet.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2216 generiert:

```cpp
// C2216.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   static int staticConst2 = 10;   // C2216
};
```

Im folgenden Beispiel wird C2216 generiert:

```cpp
// C2216b.cpp
// compile with: /clr /c
public ref class X {
   extern property int i { int get(); }   // C2216 extern not allowed on property
   typedef property int i2;   // C2216 typedef not allowed on property
};
```

Im folgenden Beispiel wird C2216 generiert:

```cpp
// C2216c.cpp
// compile with: /clr /c
public interface struct I {
   double f();
   double g();
   double h();
};

public ref struct R : I {
   virtual double f() new override { return 0.0; }   // C2216
   virtual double g() new { return 0.0; }   // OK
   virtual double h() override { return 0.0; }   // OK
};
```
