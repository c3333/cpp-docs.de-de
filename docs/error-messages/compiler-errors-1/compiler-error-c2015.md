---
title: Compilerfehler C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 5453009e1c2bd091ed3507f3c43bd7fcecd33abc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743099"
---
# <a name="compiler-error-c2015"></a>Compilerfehler C2015

zu viele Zeichen in der Konstante

Eine Zeichen Konstante enthält mehr als zwei Zeichen. Das Limit ist ein Zeichen für Standard Zeichen Konstanten und zwei Zeichen für Long-Zeichen Konstanten.

Eine Escapesequenz, z. b. \t, wird in ein einzelnes Zeichen konvertiert.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2015 generiert:

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

C2015 kann auch auftreten, wenn eine Microsoft-Erweiterung, Zeichen Konstanten, die in ganze Zahlen konvertiert werden, verwendet wird.  Im folgenden Beispiel wird C2015 generiert:

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
