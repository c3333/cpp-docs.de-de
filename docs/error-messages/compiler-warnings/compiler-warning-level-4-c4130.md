---
title: Compilerwarnung (Stufe 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 7b2fbccfd3b124220d6e310c01adace1d3e112c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219962"
---
# <a name="compiler-warning-level-4-c4130"></a>Compilerwarnung (Stufe 4) C4130

"Operator": Logische Operation mit Adresse einer Zeichenfolgenkonstanten

Das Verwenden des Operators mit der Adresse eines Zeichenfolgenliterals erzeugt unerwarteten Code.

Im folgenden Beispiel wird C4130 generiert.

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

Die- **`if`** Anweisung vergleicht den im Zeiger gespeicherten Wert `pc` mit der Adresse der Zeichenfolge "Hello", die bei jedem Auftreten der Zeichenfolge im Code separat zugeordnet wird. Die- **`if`** Anweisung vergleicht nicht die Zeichenfolge, auf die durch gezeigt wird, `pc` mit der Zeichenfolge "Hello".

Verwenden Sie zum Vergleichen von Zeichenfolgen die `strcmp` -Funktion.
