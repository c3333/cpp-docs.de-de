---
title: Compilerfehler C2718
ms.date: 11/04/2016
f1_keywords:
- C2718
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
ms.openlocfilehash: 8088fd62baeffb7d53a1be2b5bccae72913cdc12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216062"
---
# <a name="compiler-error-c2718"></a>Compilerfehler C2718

"Parameter": der tatsächliche Parameter mit __declspec ("align" ("#")) wird nicht ausgerichtet.

Der [align](../../cpp/align-cpp.md) - **`__declspec`** Modifizierer ist für Funktionsparameter nicht zulässig.

Im folgenden Beispiel wird C2718 generiert:

```cpp
// C2718.cpp
typedef struct __declspec(align(32)) AlignedStruct  {
   int i;
} AlignedStruct;

void f2(int i, ...);

void f4() {
   AlignedStruct as;

   f2(0, as);   // C2718, actual parameter is aligned
}
```
