---
title: Compilerwarnung (Stufe 1) C4293
description: Beschreibt die Gründe für die MSVC-Compilerwarnung C4293 und zeigt, wie Sie diesen Fehler beheben können.
ms.date: 07/15/2020
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 3b5a05d4a744b084f1cc34210a5374962064e85d
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446475"
---
# <a name="compiler-warning-level-1-c4293"></a>Compilerwarnung (Stufe 1) C4293

> '*Operator*': die UMSCHALT Anzahl ist negativ oder zu groß, nicht definiertes Verhalten.

Wenn eine Verschiebungs Anzahl negativ oder zu groß ist, ist das Verhalten des resultierenden Bilds nicht definiert.

## <a name="remarks"></a>Bemerkungen

Um dieses Problem zu beheben, können Sie eine Typumwandlung für den ersten Operanden verwenden, um es auf die Größe des Ergebnis Typs zu erweitern.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4293 generiert, und es werden Methoden zum Beheben von Informationen angezeigt:

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi)
{
   return (hi << 32) | lo;   // C4293

   // In C, try the following line instead:
   // return ( (unsigned __int64)hi << 32) | lo;
   // In C++, try this line instead:
   // return (static_cast<unsigned __int64>(hi) << 32) | lo;
}
```
