---
title: Compilerfehler C2488
ms.date: 11/04/2016
f1_keywords:
- C2488
helpviewer_keywords:
- C2488
ms.assetid: cd435909-43e4-43c6-a57c-5d02468ef75f
ms.openlocfilehash: 0c361db98e0ffd3f37f9e08b78f52ba7ae547030
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757110"
---
# <a name="compiler-error-c2488"></a>Compilerfehler C2488

' Identifier ': ' naked ' kann nur auf Funktionsdefinitionen angewendet werden, die nicht Mitglied sind.

Das [Naked](../../cpp/naked-cpp.md) -Attribut wurde auf eine Funktionsdeklaration angewendet.

Im folgenden Beispiel wird C2488 generiert:

```cpp
// C2488.cpp
// compile with: /c
// processor: x86
__declspec( naked ) void func();   // C2488  declaration, not definition
__declspec( naked ) void i;   // C2488  i is not a function

__declspec( naked ) void func() {}   // OK
```
