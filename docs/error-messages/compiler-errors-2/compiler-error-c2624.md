---
title: Compilerfehler C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: d97722306e5c995a4921c6eb9577d623b21c9517
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216166"
---
# <a name="compiler-error-c2624"></a>Compilerfehler C2624

lokale Klassen können nicht zum Deklarieren von externen Variablen verwendet werden.

Eine lokale Klasse oder Struktur kann nicht zum Deklarieren von Variablen verwendet werden **`extern`** .

Im folgenden Beispiel wird C2624 generiert:

```cpp
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```
