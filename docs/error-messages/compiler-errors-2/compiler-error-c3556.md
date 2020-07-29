---
title: Compilerfehler C3556
ms.date: 11/04/2016
f1_keywords:
- C3556
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
ms.openlocfilehash: 50f97c4360080f1271d9decc3b3460c06f3fec0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230817"
---
# <a name="compiler-error-c3556"></a>Compilerfehler C3556

> "*Ausdruck*": falsches Argument für "decltype"

Der Compiler kann den Typ des Ausdrucks, der das Argument für den `decltype(` *Expression* - `)` Typspezifizierer ist, nicht ableiten.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel kann der Compiler den Typ des `myFunction` -Arguments nicht ableiten, weil `myFunction` überladen ist. Um dieses Problem zu beheben, können Sie verwenden, **`static_cast`** um eine Instanz eines Zeigers auf die jeweilige überladene Funktion zu erstellen, die im Ausdruck angegeben werden soll **`decltype`** .

```cpp
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);
void myFunction(float, float);

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) {
    std::cout << "called myFunction(" << i << ")" << std::endl;
}

void myFunction(float f, float g) {
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl;
}

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```
