---
title: constexpr-Lambda-Ausdrücke inC++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 9467d9e404204012df6461adacd5dc4cdbdfe71d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179574"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr-Lambda-Ausdrücke inC++

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): ein Lambda-Ausdruck kann als **constexpr** deklariert oder in einem konstanten Ausdruck verwendet werden, wenn die Initialisierung der einzelnen Datenmember, die von ihm erfasst oder eingeführt werden, innerhalb eines konstanten Ausdrucks zulässig ist.

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

Ein Lambda-Ausdruck ist implizit **constexpr** , wenn sein Ergebnis den Anforderungen einer **constexpr** -Funktion entspricht:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Wenn ein Lambda implizit oder explizit **constexpr**ist und Sie es in einen Funktionszeiger konvertieren, ist die resultierende Funktion auch **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Funktionsobjekte in der C++-Standardbibliothek](../standard-library/function-objects-in-the-stl.md)<br/>
[Funktionsaufruf](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
