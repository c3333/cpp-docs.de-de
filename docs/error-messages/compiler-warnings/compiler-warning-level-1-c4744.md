---
title: Compilerwarnung (Stufe 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367380"
---
# <a name="compiler-warning-level-1-c4744"></a>Compilerwarnung (Stufe 1) C4744

'var' hat einen anderen Typ in 'Datei1' und 'Datei2': 'Typ1' und 'Typ2'

Eine externe Variable, auf die in zwei Dateien verwiesen oder definiert ist, weist in diesen Dateien unterschiedliche Typen auf.  Um aufzulösen, machen Sie entweder die Typdefinitionen gleich, oder ändern Sie den Variablennamen in einer der Dateien.

C4744 wird nur angezeigt, wenn Dateien mit /GL kompiliert werden.  Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
> C4744 tritt in der Regel in C-Dateien (nicht C++) auf, da in C++ ein Variablenname mit Typinformationen verziert ist.  Wenn das Beispiel (unten) als C++ kompiliert wird, wird der Linkerfehler LNK2019 angezeigt.

## <a name="example"></a>Beispiel

Dieses Beispiel enthält die erste Definition.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4744 generiert.

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
