---
title: Compilerfehler C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: e4163d68e0fbfea062279ba91e2c902855245e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220391"
---
# <a name="compiler-error-c2272"></a>Compilerfehler C2272

"Function": modifiziererer sind in statischen Element Funktionen nicht zulässig.

Eine **`static`** Member-Funktion wird mit einem Speichermodell Spezifizierer deklariert, z. b [.](../../cpp/const-cpp.md) "Konstante" oder " [flüchtig](../../cpp/volatile-cpp.md)", und solche Modifizierer sind für Element Funktionen nicht zulässig **`static`** .

Im folgenden Beispiel wird C2272 generiert:

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
