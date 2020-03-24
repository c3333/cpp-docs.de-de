---
title: Compilerwarnung (Stufe 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 6dc5e2c7a40a276e225d030bc0340fb0bfe25bb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162724"
---
# <a name="compiler-warning-level-1-c4391"></a>Compilerwarnung (Stufe 1) C4391

' Signature ': Falscher Rückgabetyp für die intrinsische Funktion, erwartet wurde ' type '.

Eine Funktionsdeklaration für eine systeminterne Compilerfunktion hatte den falschen Rückgabetyp. Das resultierende Image kann möglicherweise nicht ordnungsgemäß ausgeführt werden.

Um diese Warnung zu beheben, korrigieren Sie die Deklaration, oder löschen Sie die Deklaration, und #include Sie einfach die entsprechende Header Datei.

Im folgenden Beispiel wird C4391 generiert:

```cpp
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```
