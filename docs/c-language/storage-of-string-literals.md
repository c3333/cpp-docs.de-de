---
title: Speicherung von Zeichenfolgenliteralen
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157863"
---
# <a name="storage-of-string-literals"></a>Speicherung von Zeichenfolgenliteralen

Die Zeichen einer Literalzeichenfolge werden in Reihenfolge an zusammenhängenden Speicherorten gespeichert. Eine Escapesequenz (wie z.B. **\\\\** oder **\\"** ) innerhalb eines Zeichenfolgenliterals zählt als einzelnes Zeichen. Ein NULL-Zeichen (dargestellt durch die Escapesequenz **\0**) wird automatisch angefügt und markiert das Ende eines Zeichenfolgenliterals. (Dies geschieht bei [Übersetzungsphase](../preprocessor/phases-of-translation.md) 7.) Beachten Sie, dass der Compiler zwei identische Zeichenfolgen möglicherweise nicht an zwei verschiedenen Adressen speichert. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) erzwingt, dass der Compiler eine einzige Kopie von identischen Zeichenfolgen in die ausführbare Datei einfügt.

## <a name="remarks"></a>Hinweise

**Microsoft-spezifisch**

Zeichenfolgen haben eine statische Speicherdauer. Weitere Informationen über die Speicherdauer finden Sie unter [Speicherklassen](../c-language/c-storage-classes.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Zeichenfolgenliterale](../c-language/c-string-literals.md)
