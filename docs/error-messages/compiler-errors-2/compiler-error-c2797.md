---
title: Compilerfehler C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: 9973ddcccc69e85bdf79e0623fa4bcc1d6689032
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202078"
---
# <a name="compiler-error-c2797"></a>Compilerfehler C2797

Veralteten Die Listen Initialisierung innerhalb der Member-Initialisiererliste oder ein nicht statischer Datenmember-Initialisierer ist nicht implementiert.

Diese Warnung ist in Visual Studio 2015 veraltet. In Visual Studio 2013 und früheren Versionen implementiert der Microsoft C++ -Compiler die Listen Initialisierung weder in einer elementinitialisiererliste noch in einem nicht statischen Datenmember-Initialisierer. Vor dem Visual Studio 2013 Update 3 wurde dies im Hintergrund in einen Funktionsaufruf konvertiert, der zur Generierung von ungültigem Code führen könnte. Visual Studio 2013 Update 3 meldet dies als Fehler.

In diesem Beispiel wird C2797 generiert:

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

In diesem Beispiel wird auch die C2797:

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

Um dieses Problem zu beheben, können Sie die explizite Konstruktion von inneren Listen verwendn. Beispiel:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

Wenn Sie keine Listen-Initialisierung erfordern:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Der Compiler in Visual Studio 2013 Fall vor dem Visual Studio 2013 Update 3 hat dies nur implizit ausgeführt.)
