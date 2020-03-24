---
title: Compilerwarnung (Stufe 1) C4047
ms.date: 11/04/2016
f1_keywords:
- C4047
helpviewer_keywords:
- C4047
ms.assetid: b75ad6fb-5c93-4434-a85f-c4083051a5de
ms.openlocfilehash: 1bed592325f864e41f7dfdf2edaad86630e4b205
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164195"
---
# <a name="compiler-warning-level-1-c4047"></a>Compilerwarnung (Stufe 1) C4047

„Operator“: „Bezeichner1“ unterscheidet sich in Ebenen der Dereferenzierung von „Bezeichner2“.

Ein Zeiger kann auf eine Variable (eine Dereferenzierungsebene), auf einen anderen Zeiger zeigen, der auf eine Variable (zwei Dereferenzierungsebenen) verweist usw.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4047 generiert:

```c
// C4047.c
// compile with: /W1

int main() {
   char **p = 0;   // two levels of indirection
   char *q = 0;   // one level of indirection

   char *p2 = 0;   // one level of indirection
   char *q2 = 0;   // one level of indirection

   p = q;   // C4047
   p2 = q2;
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4047 generiert:

```c
// C4047b.c
// compile with: /W1
#include <stdio.h>

int main() {
   int i;
   FILE *myFile = NULL;
   errno_t  err = 0;
   char file_name[256];
   char *cs = 0;

   err = fopen_s(&myFile, "C4047.txt", "r");
   if ((err != 0) || (myFile)) {
      printf_s("fopen_s failed!\n");
      exit(-1);
    }
   i = fgets(file_name, 256, myFile);   // C4047
   cs = fgets(file_name, 256, myFile);   // OK
}
```
