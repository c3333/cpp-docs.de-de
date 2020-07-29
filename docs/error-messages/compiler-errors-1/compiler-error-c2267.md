---
title: Compilerfehler C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 0a72470feb79a226fe0f167364eeaea7dec9fd4d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208472"
---
# <a name="compiler-error-c2267"></a>Compilerfehler C2267

"Function": statische Funktionen mit Block Bereich sind unzulässig.

Eine lokale Funktion wird deklariert **`static`** . Statische Funktionen müssen einen globalen Gültigkeitsbereich aufweisen.

Im folgenden Beispiel wird C2267 generiert:

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
