---
title: Assemblysprachenkommentare
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 2e993bd48c7ec801abd440676c80a5bd8f7b42ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192729"
---
# <a name="assembly-language-comments"></a>Assemblysprachenkommentare

**Microsoft-spezifisch**

Anweisungen in einem **`__asm`** -Block können assemblysprachenkommentare verwenden:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Da C-Makros in eine einzelne logische Linie erweitert werden, sollten Sie die Verwendung von assemblysprachenkommentaren in Makros vermeiden. (Siehe [Definieren von __asm Blöcken als C-Makros](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Ein **`__asm`** -Block kann auch Kommentare im C-Stil enthalten. Weitere Informationen finden [Sie unter Verwenden von c oder C++ in __asm Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden der Assemblysprache in __asm Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
