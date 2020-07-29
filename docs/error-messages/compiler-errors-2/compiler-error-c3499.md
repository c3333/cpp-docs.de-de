---
title: Compilerfehler C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: 21d7424e727dab54ff507a8ec9a38db44df1806f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228842"
---
# <a name="compiler-error-c3499"></a>Compilerfehler C3499

Ein Lambda, für das ein Void-Rückgabetyp angegeben wurde, kann keinen Wert zurückgeben.

Der Compiler generiert diesen Fehler, wenn ein Lambda-Ausdruck, **`void`** der als Rückgabetyp angibt, einen Wert zurückgibt, oder wenn ein Lambda-Ausdruck mehr als eine Anweisung enthält und einen Wert zurückgibt, aber nicht seinen Rückgabetyp angibt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Lassen Sie keinen Wert vom Lambdaausdruck zurückgeben, oder

- geben Sie den Rückgabetyp des Lambdaausdrucks an, oder

- kombinieren Sie die Anweisungen, die den Text des Lambdaausdrucks darstellen, in einer einzigen Anweisung.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3499 generiert, da der Text eines Lambdaausdrucks mehrere Anweisungen enthält. Außerdem wird ein Wert zurückgegeben, ohne dass vom Lambdaausdruck der Rückgabetyp angegeben wird:

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden zwei mögliche Lösungen für den Fehler C3499 gezeigt: In der ersten Lösung wird der Rückgabetyp des Lambdaausdrucks angegeben. In der zweiten Lösungen werden die Anweisungen, die den Text des Lambdaausdrucks darstellen, in einer einzigen Anweisung kombiniert.

```cpp
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
