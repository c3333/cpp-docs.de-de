---
title: Compilerwarnung (Stufe 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: bace6057a7a2981bba2d628d8eb21c67f01c3a22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230752"
---
# <a name="compiler-warning-level-1-c4033"></a>Compilerwarnung (Stufe 1) C4033

"Funktion" muss einen Wert zurückgeben

Die Funktion gibt keinen Wert zurück. Es wird ein nicht definierter Wert zurückgegeben.

Funktionen, die **`return`** ohne Rückgabewert verwenden, müssen als Typ deklariert werden **`void`** .

Dieser Fehler gilt für die C-Sprachcode.

Im folgenden Beispiel wird C4033 generiert:

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
