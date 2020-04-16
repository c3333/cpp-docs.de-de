---
title: Bereich von char-Werten
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 8cb2609aca910056b5243fddc868710581e576e7
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480905"
---
# <a name="range-of-char-values"></a>Bereich von char-Werten

**ANSI 3.2.1.1** Gibt an, ob ein **"plain"-Zeichen** den gleichen Wertebereich wie ein **signiertes Zeichen** oder ein **nicht signiertes Zeichen** hat

Alle Zeichenwerte mit Vorzeichen liegen im Bereich zwischen –128 und 127. Alle nicht signierten Zeichenwerte liegen im Bereich von 0 bis 255.

Die [`/J`](../build/reference/j-default-char-type-is-unsigned.md) Compileroption ändert den Standardtyp für **char** von **signed char** in **unsigned char**.

## <a name="see-also"></a>Weitere Informationen

[Zeichen](../c-language/characters.md)
