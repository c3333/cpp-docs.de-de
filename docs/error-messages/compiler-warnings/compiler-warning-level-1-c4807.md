---
title: Compilerwarnung (Stufe 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 2424d076be0914a68c3227566cb851b7ab64cc0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175037"
---
# <a name="compiler-warning-level-1-c4807"></a>Compilerwarnung (Stufe 1) C4807

"Operation": Unsichere Kombination von Typ "Typ" und signiertem Bitfeld des Typs "Typ"

Diese Warnung wird erzeugt, wenn ein vorzeichenbehaftetes Bitfeld der Länge 1 mit einer `bool` -Variablen verglichen wird. Da ein vorzeichenbehaftetes Bitfeld der Länge 1 nur die Werte -1 oder 0 enthalten kann, ist der Vergleich mit einem `bool`-Wert nicht unproblematisch. Keine Warnungen werden dagegen erzeugt, wenn `bool` -Werte mit vorzeichenlosen Bitfeldern der Länge 1 verglichen werden, da diese mit `bool` identisch sind und nur 0 oder 1 enthalten können.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4807 generiert:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
