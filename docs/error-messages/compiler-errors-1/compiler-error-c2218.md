---
title: Compilerfehler C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: db14c37992fc1e2dd409c653d622d3419fcae4f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206647"
---
# <a name="compiler-error-c2218"></a>Compilerfehler C2218

"__vectorcall" kann nicht zusammen mit "/arch:IA32" verwendet werden.

Die Aufrufkonvention `__vectorcall` wird nur in nativem Code auf x86- und x64-Prozessoren unterstützt, die zusätzlich SIMD-Streamingerweiterungen 2 (SSE2) und höher einschließen. Weitere Informationen finden Sie unter [__vectorcall](../../cpp/vectorcall.md).

Um diesen Fehler zu beheben, ändern Sie die Compileroptionen in die Befehlssätze Ziel SSE2, AVX oder AVX2. Weitere Informationen finden Sie unter [/arch (x86)](../../build/reference/arch-x86.md).
