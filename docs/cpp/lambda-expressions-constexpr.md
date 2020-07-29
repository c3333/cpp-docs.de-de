---
title: constexpr-Lambda Ausdrücke in C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 24c70732093447649b3cfb460f63b2181efdf806
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213345"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr-Lambda Ausdrücke in C++

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): ein Lambda-Ausdruck kann als **`constexpr`** oder in einem konstanten Ausdruck verwendet werden, wenn die Initialisierung der einzelnen Datenmember, die von ihm erfasst oder eingeführt werden, innerhalb eines konstanten Ausdrucks zulässig ist.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Ein Lambda-Ausdruck ist implizit, **`constexpr`** wenn sein Ergebnis den Anforderungen einer **`constexpr`** Funktion entspricht:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Wenn ein Lambda implizit oder explizit ist **`constexpr`** und Sie es in einen Funktionszeiger konvertieren, ist die resultierende Funktion auch **`constexpr`** :

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Siehe auch

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Funktions Objekte in der C++-Standard Bibliothek](../standard-library/function-objects-in-the-stl.md)<br/>
[Funktionsaufrufe](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
