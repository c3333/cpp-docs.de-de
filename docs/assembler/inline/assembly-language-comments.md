---
title: Assemblysprachenkommentare
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169603"
---
# <a name="assembly-language-comments"></a>Assemblysprachenkommentare

**Microsoft-spezifisch**

Anweisungen in einem `__asm`-Block können assemblysprachenkommentare verwenden:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Da C-Makros in eine einzelne logische Linie erweitert werden, sollten Sie die Verwendung von assemblysprachenkommentaren in Makros vermeiden. (Siehe [Definieren von __asm Blöcken als C-Makros](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Ein `__asm`-Block kann auch Kommentare im C-Stil enthalten. Weitere Informationen finden Sie unter [using C or C++ in __asm Blocks](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
