---
title: Compilerfehler C2166
ms.date: 11/04/2016
f1_keywords:
- C2166
helpviewer_keywords:
- C2166
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
ms.openlocfilehash: a292a7d654861c265457ad26b009ae6f4b9cb54e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216335"
---
# <a name="compiler-error-c2166"></a>Compilerfehler C2166

L-Wert gibt ein const-Objekt an

Der Code versucht, ein deklariertes Element zu ändern **`const`** .

Im folgenden Beispiel wird C2166 generiert:

```cpp
// C2166.cpp
int f();
int main() {
   ( (const int&) 1 ) = 5;   // C2166
}
```
