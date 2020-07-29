---
title: Compilerfehler C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225474"
---
# <a name="compiler-error-c2464"></a>Compilerfehler C2464

"Bezeichner": "New" kann nicht zum Zuordnen eines Verweises verwendet werden.

Dem Operator wurde ein Verweis Bezeichner zugeordnet **`new`** . Verweise sind keine Speicher Objekte und können daher keinen **`new`** Zeiger darauf zurückgeben. Verwenden Sie die standardmäßige Variablen Deklarations Syntax zum Deklarieren eines Verweises.

Im folgenden Beispiel wird C2464 generiert:

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
