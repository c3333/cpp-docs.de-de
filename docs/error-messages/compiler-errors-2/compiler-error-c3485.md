---
title: Compilerfehler C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2117832ffd5a90612e9745a3706f01e3b5d1b18d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197669"
---
# <a name="compiler-error-c3485"></a>Compilerfehler C3485

Eine Lambdadefinition kann keine CV-Qualifizierer aufweisen.

Sie können keinen- **`const`** oder- **`volatile`** Qualifizierer als Teil der Definition eines Lambda-Ausdrucks verwenden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den- **`const`** oder- **`volatile`** Qualifizierer aus der Definition des Lambda-Ausdrucks.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3485 generiert, weil der **`const`** Qualifizierer als Teil der Definition eines Lambda-Ausdrucks verwendet wird:

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Weitere Informationen

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
