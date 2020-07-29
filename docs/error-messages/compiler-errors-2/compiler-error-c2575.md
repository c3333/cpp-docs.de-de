---
title: Compilerfehler C2575
ms.date: 11/04/2016
f1_keywords:
- C2575
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
ms.openlocfilehash: c00ae519f5e6b595ec07d6a617813a3ae79ab72d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221132"
---
# <a name="compiler-error-c2575"></a>Compilerfehler C2575

"Bezeichner": nur Element Funktionen und Basen können virtuell sein.

Eine globale Funktion oder Klasse wird deklariert **`virtual`** . Dies ist nicht zulässig.

Im folgenden Beispiel wird C2575 generiert:

```cpp
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```
