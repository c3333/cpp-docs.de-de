---
title: Compilerfehler C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: 95b3a3bae531170bf12c0e34613ad41f742304bb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218246"
---
# <a name="compiler-error-c2352"></a>Compilerfehler C2352

'class::function': Unzulässiger Aufruf einer nicht statischen Memberfunktion

Eine Member-Funktion, die als **`static`** nicht statische Member-Funktion bezeichnet wird. Oder es wurde eine nicht statische Memberfunktion von außerhalb der Klasse als eine statische Funktion aufgerufen.

Im folgenden Beispiel wird C2352 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

Im folgenden Beispiel wird C2352 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```
