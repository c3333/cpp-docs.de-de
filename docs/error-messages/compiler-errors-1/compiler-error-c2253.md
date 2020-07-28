---
title: Compilerfehler C2253
ms.date: 11/04/2016
f1_keywords:
- C2253
helpviewer_keywords:
- C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
ms.openlocfilehash: 3110c608879d43405d619f7e3beca03ecab8cbee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214710"
---
# <a name="compiler-error-c2253"></a>Compilerfehler C2253

"Function": ein reiner Spezifizierer oder ein abstrakter Überschreibungsspezifizierer ist nur für eine virtuelle

Eine nicht virtuelle Funktion wird als rein angegeben **`virtual`** .

Im folgenden Beispiel wird C2253 generiert:

```cpp
// C2253.cpp
// compile with: /c
class A {
public:
   void func1() = 0;   // C2253 not virtual
   virtual void func2() = 0;   // OK
};
```

Im folgenden Beispiel wird C2253 generiert:

```cpp
// C2253_2.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_3 {
      int get() abstract;   // C2253
      // try the following line instead
      // virtual int get() abstract;

      void set(int i) abstract;   // C2253
      // try the following line instead
      // virtual void set(int i) abstract;
   }
};
```
