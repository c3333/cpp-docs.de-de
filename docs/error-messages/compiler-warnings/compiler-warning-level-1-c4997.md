---
title: Compilerwarnung (Stufe 1) C4997
ms.date: 11/04/2016
f1_keywords:
- C4997
helpviewer_keywords:
- C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
ms.openlocfilehash: ba5b2ec48c29b40ecb690cf9d222e518f91d219f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174400"
---
# <a name="compiler-warning-level-1-c4997"></a>Compilerwarnung (Stufe 1) C4997

„class“: Die Co-Klasse implementiert keine COM- oder Pseudoschnittstelle.

Eine mit dem [coclass](../../windows/coclass.md) -Attribut markierte Klasse hat keine Schnittstelle implementiert.

Im folgenden Beispiel wird C4997 generiert.

```cpp
// C4997.cpp
// compile with: /WX
// to resolve this C4997, uncomment all code
#include <objbase.h>

[ object ]
__interface I {
   HRESULT func();
};

[ coclass ]
struct C /*: I*/ {
   /*
   HRESULT func() {
      return S_OK;
   }
   */
};   // C4997
```
