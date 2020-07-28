---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: e12855127e417472eb88c951b71881240b808013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214203"
---
# <a name="__noop"></a>__noop

**Microsoft-spezifisch**

Der systeminterne Wert **`__noop`** gibt an, dass eine Funktion ignoriert werden soll. Die Argumentliste wird analysiert, aber es wird kein Code für die Argumente generiert. Es ist für die Verwendung in globalen Debugfunktionen vorgesehen, die eine Variable Anzahl von Argumenten akzeptieren.

Der Compiler konvertiert den systeminternen zum Zeitpunkt der **`__noop`** Kompilierung in 0.

## <a name="example"></a>Beispiel

Der folgende Code zeigt, wie Sie verwenden können **`__noop`** .

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[Schlüsselwörter](../cpp/keywords-cpp.md)
