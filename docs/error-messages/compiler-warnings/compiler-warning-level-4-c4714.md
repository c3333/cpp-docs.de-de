---
title: Compilerwarnung (Stufe 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 286a9e6e12643d3dadd070e7c4cf4b2dd350c02c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219858"
---
# <a name="compiler-warning-level-4-c4714"></a>Compilerwarnung (Stufe 4) C4714

> die Funktion "Function" ist als __forceinline nicht Inline gekennzeichnet.

Die angegebene Funktion wurde für die Inline Erweiterung ausgewählt, aber der Compiler hat das Inlining nicht durchgeführt.

Obwohl **`__forceinline`** für den Compiler ein stärkerer Hinweis ist als **`__inline`** , wird Inlining nach wie vor mit dem Ermessen des Compilers ausgeführt. es werden jedoch keine Heuristik verwendet, um die Vorteile des Inlining dieser Funktion zu bestimmen.

In einigen Fällen wird der Compiler eine bestimmte Funktion aus mechanischen Gründen nicht Inline Inline. Der Compiler wird z. b. nicht Inline:

- Eine Funktion, wenn Sie sowohl SEH als auch C++ EH mischen würde.

- Einige Funktionen mit kopierten Kopier Objekten wurden als Wert weitergegeben, wenn-GX/EHs/EHa aktiviert ist.

- Funktionen, die ein nicht windable-Objekt nach Wert zurückgeben, wenn-GX/EHs/EHa auf ON festgelegt ist.

- Funktionen mit der Inlineassembly beim Kompilieren ohne-og/Ox/o1/o2.

- Funktionen mit einer Variablen Argumentliste.

- Eine Funktion mit einer- **`try`** Anweisung (C++ Exception Handling).

Im folgenden Beispiel wird C4714 generiert:

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
