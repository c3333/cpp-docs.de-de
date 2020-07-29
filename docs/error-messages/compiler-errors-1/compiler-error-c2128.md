---
title: Compilerfehler C2128
ms.date: 11/04/2016
f1_keywords:
- c2128
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
ms.openlocfilehash: 38cfb3ff81073a123f2d8c3c83c29c42c27d9dc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225565"
---
# <a name="compiler-error-c2128"></a>Compilerfehler C2128

"Function": alloc_text/same_seg nur auf Funktionen mit C-Verknüpfung anwendbar.

`#pragma alloc_text`kann nur mit Funktionen verwendet werden, die für die C-Verknüpfung deklariert wurden.

Im folgenden Beispiel wird C2128 generiert:

```cpp
// C2128.cpp
// compile with: /c

// Delete the following line to resolve.
void func();
// #pragma alloc_text("my segment", func)   // C2128

extern "C" {
void func();
}

#pragma alloc_text("my segment", func)
void func() {}
```
