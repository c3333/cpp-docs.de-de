---
title: Compilerfehler C2802
ms.date: 11/04/2016
f1_keywords:
- C2802
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
ms.openlocfilehash: f872a4753907cd78c9118c22498777d5acc5b2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214580"
---
# <a name="compiler-error-c2802"></a>Compilerfehler C2802

der statische Member "Operator Operator" weist keine formalen Parameter auf.

Ein Operator, der von einer Member-Funktion deklariert wird, **`static`** muss mindestens einen Parameter aufweisen.

Im folgenden Beispiel wird C2802 generiert:

```cpp
// C2802.cpp
// compile with: /clr /c
ref class A {
   static operator+ ();   // C2802
   static operator+ (A^, A^);   // OK
};
```
