---
title: Compilerfehler C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 97f3290ef8bcb6a91442effdbf84261c03545ce2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87209525"
---
# <a name="compiler-error-c2218"></a>Compilerfehler C2218

> "__vectorcall" kann nicht zusammen mit "/arch:IA32" verwendet werden.

Die **`__vectorcall`** Aufruf Konvention wird nur in nativem Code auf x86-und x64-Prozessoren unterstützt, die Streaming SIMD Extensions 2 (SSE2) und höher enthalten. Weitere Informationen finden Sie unter [`__vectorcall`](../../cpp/vectorcall.md).

Um diesen Fehler zu beheben, ändern Sie die Compileroptionen in die Befehlssätze Ziel SSE2, AVX oder AVX2. Weitere Informationen finden Sie unter [ `/arch` (x86)](../../build/reference/arch-x86.md).
