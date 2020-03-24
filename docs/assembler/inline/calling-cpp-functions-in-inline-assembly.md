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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169577"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Aufrufen von C++-Funktionen in der Inlineassembly

**Microsoft-spezifisch**

Ein `__asm`-Block kann nur globale C++ Funktionen aufzurufen, die nicht überladen sind. Wenn Sie eine überladene C++ globale Funktion oder C++ eine Member-Funktion aufzurufen, gibt der Compiler einen Fehler aus.

Sie können auch alle Funktionen aufzurufen, die mit **extern "C"** -Verknüpfung deklariert wurden. Dies ermöglicht es einem `__asm` Block innerhalb C++ eines Programms, die C-Bibliotheksfunktionen aufzurufen, da alle Standard Header Dateien die Bibliotheksfunktionen so deklarieren, dass Sie **externe "C"** -Verknüpfungen aufweisen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Inlineassembler](../../assembler/inline/inline-assembler.md)<br/>
