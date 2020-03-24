---
title: Compilerwarnung (Stufe 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: a62bfdb6b9b29abf047e7690179978cb9516d477
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186880"
---
# <a name="compiler-warning-level-1-c4392"></a>Compilerwarnung (Stufe 1) C4392

"Signature": falsche Anzahl von Argumenten für die intrinsische Funktion, erwartete "Number"-Argumente.

Eine Funktionsdeklaration für eine systeminterne Compilerfunktion weist die falsche Anzahl von Argumenten auf. Das resultierende Image kann möglicherweise nicht ordnungsgemäß ausgeführt werden.

Um diese Warnung zu beheben, korrigieren Sie die Deklaration, oder löschen Sie die Deklaration, und #include Sie einfach die entsprechende Header Datei.

Im folgenden Beispiel wird C4392 generiert:

```cpp
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```
