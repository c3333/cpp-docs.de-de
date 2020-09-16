---
title: Compilerwarnung (Stufe 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 25b97cfb50847a0929f3d3a97b822209e6a11900
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686677"
---
# <a name="compiler-warning-level-4-c4239"></a>Compilerwarnung (Stufe 4) C4239

nicht dem Standard entsprechende Erweiterung verwendet: ' Token ': Konvertierung von ' type ' in ' type '

Diese Typkonvertierung ist vom C++-Standard nicht zulässig, aber hier als Erweiterung zulässig. Auf diese Warnung folgt immer mindestens eine Erklärung, in der die Verletzung der Sprachregel beschrieben wird.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C4239 generiert.

```cpp
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

Die Konvertierung eines ganzzahligen Typs in einen Aufzählungstyp ist nicht streng zulässig.

Im folgenden Beispiel wird C4239 generiert.

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```
