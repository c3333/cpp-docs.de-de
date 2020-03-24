---
title: Segmentverweise in der Inlineassembly
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169252"
---
# <a name="segment-references-in-inline-assembly"></a>Segmentverweise in der Inlineassembly

**Microsoft-spezifisch**

Sie müssen auf Segmente durch Register anstatt nach Name verweisen (der Segment Name `_TEXT` beispielsweise ungültig). Segment Überschreibungen müssen das Register explizit wie in es: [BX] verwenden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Verwenden der Assemblysprache in __asm-Blöcken](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
