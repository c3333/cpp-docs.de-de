---
title: Compilerwarnung (Stufe 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164351"
---
# <a name="compiler-warning-level-1-c4033"></a>Compilerwarnung (Stufe 1) C4033

"Funktion" muss einen Wert zurückgeben

Die Funktion gibt keinen Wert zurück. Es wird ein nicht definierter Wert zurückgegeben.

Funktionen, in denen `return` ohne einen Rückgabewert verwendet wird, müssen mit dem Typ `void`deklariert werden.

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
