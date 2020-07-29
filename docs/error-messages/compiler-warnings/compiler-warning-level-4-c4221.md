---
title: Compilerwarnung (Stufe 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: e925f315e8506453403b0a0eda75b7c2956cc05c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219936"
---
# <a name="compiler-warning-level-4-c4221"></a>Compilerwarnung (Stufe 4) C4221

nicht dem Standard entsprechende Erweiterung: "Bezeichner": kann nicht mit der Adresse der automatischen Variablen initialisiert werden.

Mit den standardmäßigen Microsoft-Erweiterungen (/Ze) können Sie einen Aggregations Typ (**Array**, **`struct`** oder **`union`** ) mit der Adresse einer lokalen (automatischen) Variablen initialisieren.

## <a name="example"></a>Beispiel

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Diese Initialisierungen sind unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) ungültig.
