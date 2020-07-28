---
title: Aufrufen von C++-Funktionen in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 781b60c8973593039c0fdfa2f457170e95048597
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192534"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Aufrufen von C++-Funktionen in der Inlineassembly

**Microsoft-spezifisch**

Ein- **`__asm`** Block kann nur globale C++-Funktionen aufzurufen, die nicht überladen sind. Wenn Sie eine überladene globale C++-Funktion oder eine C++-Member-Funktion aufzurufen, gibt der Compiler einen Fehler aus.

Sie können auch alle Funktionen aufzurufen, die mit **extern "C"** -Verknüpfung deklariert wurden. Dadurch kann ein **`__asm`** Block in einem C++-Programm die C-Bibliotheksfunktionen aufzurufen, da alle Standard Header Dateien die Bibliotheksfunktionen als **externe "C"** -Verknüpfung deklarieren.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Inline Assembler](../../assembler/inline/inline-assembler.md)<br/>
