---
title: Compilerwarnung (Stufe 1) C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: e8ef8c75a5e065f4f1679219d0d5fe57e5cfe86c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162958"
---
# <a name="compiler-warning-level-1-c4329"></a>Compilerwarnung (Stufe 1) C4329

__declspec (align ()) wird bei der Aufzählung ignoriert.

Die Verwendung des [align](../../cpp/align-cpp.md) -Schlüssel Worts des [__declspec](../../cpp/declspec.md) Modifizierers ist in einem `enum`nicht zulässig. Im folgenden Beispiel wird C4329 generiert:

```cpp
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```
