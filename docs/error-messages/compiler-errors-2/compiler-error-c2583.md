---
title: Compilerfehler C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: 0cb021dcba4d050afb943c03ba6b4dca053bcbb8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206847"
---
# <a name="compiler-error-c2583"></a>Compilerfehler C2583

' Identifier ': ' this '-Zeiger ist für Konstruktoren/Dekonstruktoren unzulässig.

Ein Konstruktor oder Dekonstruktor wird als **`const`** oder deklariert **`volatile`** . Dies ist nicht zulässig.

Im folgenden Beispiel wird C2583 generiert:

```cpp
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```
