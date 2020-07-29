---
title: Compilerfehler C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 3794a1ce0fcbe60c06cb3efca45a3081e85c17ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210019"
---
# <a name="compiler-error-c2180"></a>Compilerfehler C2180

steuernder Ausdruck ist vom Typ "type".

Der steuernde Ausdruck in einer-,-,- **`if`** **`while`** oder- **`for`** **`do`** Anweisung ist ein Ausdruck **`void`** , der in umgewandelt wird. Um dieses Problem zu beheben, ändern Sie den steuernden Ausdruck in einen, der einen **`bool`** oder einen Typ erzeugt, der in konvertiert werden kann **`bool`** .

Im folgenden Beispiel wird C2180 generiert:

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
