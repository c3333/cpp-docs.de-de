---
title: Compilerwarnung (Stufe 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: 6772e384b5908cbe81f85758f86eabe4c8240e6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163322"
---
# <a name="compiler-warning-level-1-c4186"></a>Compilerwarnung (Stufe 1) C4186

\#Import-Attribut "Attribut" erfordert Anzahl Argumente. erten

Ein `#import` -Attribut weist die falsche Anzahl von Argumenten auf.

## <a name="example"></a>Beispiel

```cpp
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

Das `no_namespace` -Attribut akzeptiert keine Argumente. Das **rename** -Attribut erhält nur zwei Argumente.
