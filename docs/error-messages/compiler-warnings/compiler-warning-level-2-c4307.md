---
title: Compilerwarnung (Stufe 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: f6e06acaf43708d6c0da6d67531b6c4b9f202971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161879"
---
# <a name="compiler-warning-level-2-c4307"></a>Compilerwarnung (Stufe 2) C4307

"Operator": ganzzahliger konstanter Überlauf

Der-Operator wird in einem Ausdruck verwendet, der dazu führt, dass eine ganzzahlige Konstante den zugeordneten Speicherplatz überlagert. Möglicherweise müssen Sie einen größeren Typ für die Konstante verwenden. Ein **int** -Wert mit Vorzeichen enthält einen kleineren Wert als ein `unsigned int`, da der **signierte int** -Wert ein Bit zur Darstellung des Zeichens verwendet.

Im folgenden Beispiel wird C4307 generiert:

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```
