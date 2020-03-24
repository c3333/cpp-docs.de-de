---
title: Compilerwarnung (Stufe 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: c3ddc861e5da271903372eac1ef1e8f6916e06df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199367"
---
# <a name="compiler-warning-level-1-c4838"></a>Compilerwarnung (Stufe 1) C4838

die Konvertierung von ' TYPE_1 ' in ' TYPE_2 ' erfordert eine einschränkende Konvertierung.

Beim Verwenden der Aggregat-oder Listen Initialisierung wurde eine implizite einschränkende Konvertierung gefunden.

Die Programmiersprache C ermöglicht implizite einschränkende Konvertierungen in Zuweisungen und Initialisierung und C++ folgt, obwohl eine unerwartete Einschränkung eine Ursache für viele Code Fehler ist. Um Code sicherer zu machen, C++ erfordert der Standard eine Diagnose Meldung, wenn eine einschränkende Konvertierung in einer Initialisierungs Liste erfolgt. In Visual C++ist die Diagnose ein [Compilerfehler C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) bei Verwendung der von Visual Studio 2015 unterstützten Uniform Initialisierung-Syntax. Der Compiler generiert eine Warnung C4838 bei Verwendung der von Visual Studio 2013 unterstützten List-oder Aggregat Initialisierungs Syntax.

Eine einschränkende Konvertierung kann in Ordnung sein, wenn Sie wissen, dass der mögliche Bereich der konvertierten Werte in das Ziel passen kann. In diesem Fall wissen Sie mehr als der Compiler. Wenn Sie eine einschränkende Konvertierung absichtlich vornehmen, machen Sie Ihre Absichten mithilfe einer statischen Umwandlung explizit. Andernfalls weist diese Warnmeldung fast immer darauf hin, dass ein Fehler in Ihrem Code vorhanden ist. Sie können dieses Problem beheben, indem Sie sicherstellen, dass die initialisierten Objekte über Typen verfügen, die groß genug sind, um die Eingaben zu verarbeiten.

Im folgenden Beispiel wird C4838 generiert und eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```
