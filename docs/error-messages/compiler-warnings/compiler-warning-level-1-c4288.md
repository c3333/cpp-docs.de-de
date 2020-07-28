---
title: Compilerwarnung (Stufe 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: a732614ac5d71168ece8ada8e468afa5ba54c1f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220079"
---
# <a name="compiler-warning-level-1-c4288"></a>Compilerwarnung (Stufe 1) C4288

> nicht dem Standard entsprechende Erweiterung: "var": die Schleifen Steuerungs Variable, die in der for-Schleife deklariert wurde, wird außerhalb des for-Schleifen Bereichs verwendet. Sie steht in Konflikt mit der Deklaration im äußeren Gültigkeitsbereich.

Beim Kompilieren mit [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) und **/Zc: forScope-** wurde eine in einer **`for`** -Schleife deklarierte Variable nach dem [for](../../cpp/for-statement-cpp.md)-Schleifen Bereich verwendet. Eine Microsoft-Erweiterung der C++-Sprache ermöglicht es, dass diese Variable im Gültigkeitsbereich bleibt, und C4288 erinnert Sie daran, dass die erste Deklaration der Variablen nicht verwendet wird.

[`/Zc:forScope`](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)Informationen zum Angeben der Microsoft-Erweiterung in **`for`** Schleifen mit "/Ze" finden Sie unter.

Im folgenden Beispiel wird C4288 generiert:

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```
