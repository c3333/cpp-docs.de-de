---
title: Compilerfehler C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: af9c0f0395e29c384ddc06f9a029f29c921e71c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221236"
---
# <a name="compiler-error-c2319"></a>Compilerfehler C2319

Auf 'try/catch' muss eine zusammengesetzte Anweisung folgen. '{' fehlt

**`try`** Nach der-oder-Anweisung wurde kein-oder- **`catch`** Block gefunden **`try`** **`catch`** . Der Block muss in geschweifte Klammern eingeschlossen werden.

Im folgenden Beispiel wird C2319 generiert:

```cpp
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```
