---
title: Compilerwarnung (Stufe 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 54baf35eaeb5ef2c8add024f25c059480d60617b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186562"
---
# <a name="compiler-warning-level-1-c4508"></a>Compilerwarnung (Stufe 1) C4508

"Function": Funktion sollte einen Wert zurückgeben. der Rückgabetyp "void" wird angenommen

Für die Funktion wurde kein Rückgabetyp angegeben. In diesem Fall sollte auch C4430 ausgelöst werden, und der Compiler implementiert die von C4430 gemeldete Korrektur (Standardwert ist int).

Um diese Warnung zu beheben, deklarieren Sie explizit den Rückgabetyp der Funktionen.

Im folgenden Beispiel wird C4508 generiert:

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
