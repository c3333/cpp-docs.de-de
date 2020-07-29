---
title: Compilerwarnung (Stufe 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: c4cb71355b4f3dca66c56ed4b89012ca9b9e646d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197045"
---
# <a name="compiler-warning-level-1-c4090"></a>Compilerwarnung (Stufe 1) C4090

"Operation": unterschiedliche Modifizierer-Qualifizierer

Eine Variable, die in einem Vorgang verwendet wird, wird mit einem angegebenen Modifizierer definiert, der verhindert, dass Sie ohne Erkennung durch den Compiler geändert wird. Der Ausdruck wird ohne Änderung kompiliert.

Diese Warnung kann verursacht werden, wenn ein Zeiger auf ein- **`const`** Element oder ein- **`volatile`** Element einem Zeiger zugewiesen wird, der nicht als Verweis auf oder deklariert ist **`const`** **`volatile`** .

Diese Warnung wird für C-Programme ausgegeben. In einem C++-Programm gibt der Compiler einen Fehler aus: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Im folgenden Beispiel wird C4090 generiert:

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```
