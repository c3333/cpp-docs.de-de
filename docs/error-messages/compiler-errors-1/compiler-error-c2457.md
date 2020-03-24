---
title: Compilerfehler C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205243"
---
# <a name="compiler-error-c2457"></a>Compilerfehler C2457

> "*Makro*": ein vordefiniertes Makro kann nicht außerhalb eines Funktions Texts stehen.

Sie haben versucht, ein vordefiniertes Makro, [ &#95; &#95;z&#95;](../../preprocessor/predefined-macros.md). b. eine Funktion, in einem globalen Raum zu verwenden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2457 generiert und außerdem die korrekte Verwendung veranschaulicht:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
