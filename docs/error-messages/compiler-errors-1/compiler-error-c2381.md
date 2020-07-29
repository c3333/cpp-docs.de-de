---
title: Compilerfehler C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: a36655b0b3a28536538998656d7ce354c409d07c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225526"
---
# <a name="compiler-error-c2381"></a>Compilerfehler C2381

"Function": Neudefinition; __declspec (noreturn) unterscheidet sich

Eine Funktion wurde deklariert und dann definiert, aber die Definition hat den [noreturn](../../cpp/noreturn.md) - **`__declspec`** Modifizierer verwendet. Die Verwendung von `noreturn` stellt eine Neudefinition der-Funktion dar. die Deklaration und Definition müssen bei der Verwendung von zustimmen `noreturn` .

Im folgenden Beispiel wird C2381 generiert:

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
