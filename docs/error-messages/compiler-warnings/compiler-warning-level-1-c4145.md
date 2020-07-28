---
title: Compilerwarnung (Stufe 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: 19d2d1a018c7ee981f83aa6fa0914f1241c55538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220105"
---
# <a name="compiler-warning-level-1-c4145"></a>Compilerwarnung (Stufe 1) C4145

"Ausdruck1": Relationaler Ausdruck als Schalterausdruck; mögliche Verwechslung mit "Ausdruck2"

Eine- **`switch`** Anweisung verwendet einen relationalen Ausdruck als Steuerelement Ausdruck, der einen booleschen Wert für die Anweisungen zur Folge hat **`case`** . Meinten Sie *Ausdruck2*?

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4145 generiert:

```cpp
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```
