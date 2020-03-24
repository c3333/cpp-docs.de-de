---
title: Compilerwarnung (Stufe 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: 45ed4817dbf2c7ecd63cd0c669d6e1cf768184bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174049"
---
# <a name="compiler-warning-level-4-c4204"></a>Compilerwarnung (Stufe 4) C4204

nicht dem Standard entsprechende Erweiterung: nicht konstanter Aggregat Initialisierer

Mit Microsoft Extensions (/Ze) können Sie Aggregat Typen (Arrays, Strukturen, Unions und Klassen) mit Werten initialisieren, die keine Konstanten sind.

## <a name="example"></a>Beispiel

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

Diese Initialisierungen sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
