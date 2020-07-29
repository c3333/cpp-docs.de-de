---
title: Compilerfehler C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 0a7c711fa399c1bf31bc9de61f0b77ad19172a73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206912"
---
# <a name="compiler-error-c2577"></a>Compilerfehler C2577

"Member": der destrukturtor/Finalizer kann keinen Rückgabetyp aufweisen.

Ein debugtor oder Finalizer kann nicht den Wert **`void`** oder einen anderen Typ zurückgeben. Entfernen Sie die- **`return`** Anweisung aus der dekonstruktordefinition.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2577 generiert.

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
