---
title: Compilerfehler C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206014"
---
# <a name="compiler-error-c2397"></a>Compilerfehler C2397

die Konvertierung von ' TYPE_1 ' in ' TYPE_2 ' erfordert eine einschränkende Konvertierung.

Bei Verwendung der einheitlichen Initialisierung wurde eine implizite einschränkende Konvertierung gefunden.

Die Programmiersprache C ermöglicht implizite einschränkende Konvertierungen in Zuweisungen und Initialisierung und C++ folgt, obwohl eine unerwartete Einschränkung eine Ursache für viele Code Fehler ist. Um Code sicherer zu machen, C++ erfordert der Standard eine Diagnose Meldung, wenn eine einschränkende Konvertierung in einer Initialisierungs Liste erfolgt. In Visual C++ist die Diagnose ein Compilerfehler C2397 bei Verwendung der von Visual Studio 2015 unterstützten Uniform Initialisierung-Syntax. Der Compiler generiert [Compilerwarnung (Stufe 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) bei Verwendung der von Visual Studio 2013 unterstützten List-oder Aggregat Initialisierungs Syntax.

Eine einschränkende Konvertierung kann in Ordnung sein, wenn Sie wissen, dass der mögliche Bereich der konvertierten Werte in das Ziel passen kann. In diesem Fall wissen Sie mehr als der Compiler. Wenn Sie eine einschränkende Konvertierung absichtlich vornehmen, machen Sie Ihre Absichten mithilfe einer statischen Umwandlung explizit. Andernfalls gibt diese Fehlermeldung fast immer an, dass ein Fehler in Ihrem Code vorliegt. Sie können dieses Problem beheben, indem Sie sicherstellen, dass die initialisierten Objekte über Typen verfügen, die groß genug sind, um die Eingaben zu verarbeiten.

Im folgenden Beispiel wird C2397 generiert und eine Möglichkeit gezeigt, Sie zu beheben:

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
