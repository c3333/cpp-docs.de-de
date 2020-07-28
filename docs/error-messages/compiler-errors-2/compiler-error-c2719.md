---
title: Compilerfehler C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: a0a993069a0bd232154cf6c1b365c0828d9bede8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220248"
---
# <a name="compiler-error-c2719"></a>Compilerfehler C2719

'parameter': formeller Parameter mit __declspec(align('#')) wird nicht ausgerichtet

Der [align](../../cpp/align-cpp.md) - **`__declspec`** Modifizierer ist für Funktionsparameter nicht zulässig. Die Funktionsparameterausrichtung wird durch die verwendete Aufrufkonvention gesteuert. Weitere Informationen finden Sie unter [Aufrufen von Konventionen](../../cpp/calling-conventions.md).

Im folgenden Beispiel wird C2719 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```
