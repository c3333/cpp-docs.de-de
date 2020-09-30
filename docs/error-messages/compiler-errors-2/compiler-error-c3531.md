---
title: Compilerfehler C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 4537c6c76814f2aeb8f8d62579caec86785de252
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510133"
---
# <a name="compiler-error-c3531"></a>Compilerfehler C3531

' Symbol ': ein Symbol, dessen Typ ' Auto ' enthält, muss einen Initialisierer aufweisen.

Die angegebene Variable weist keinen initialisiererausdruck auf.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Geben Sie einen initialisiererausdruck an, z. b. eine einfache Zuweisung, die eine Gleichheitszeichen Syntax verwendet, wenn Sie die Variable deklarieren.

## <a name="example"></a>Beispiel

Das folgende Beispiel ergibt C3531, weil die Variablen `x1` , `y1, y2, y3` und `z2` nicht initialisiert sind.

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-cpp.md)
