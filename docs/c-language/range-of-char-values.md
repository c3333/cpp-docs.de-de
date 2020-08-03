---
title: Bereich von char-Werten
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 085f7a319cb193f9d9d744d6e896062e550404cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227802"
---
# <a name="range-of-char-values"></a>Bereich von char-Werten

**ANSI 3.2.1.1** Ob ein einfacher **`char`** -Wert denselben Wertebereich wie ein **`signed char`** -Wert oder ein **`unsigned char`** -Wert aufweist

Alle Zeichenwerte mit Vorzeichen liegen im Bereich zwischen –128 und 127. Alle nicht signierten Zeichenwerte liegen im Bereich von 0 bis 255.

Die [`/J`](../build/reference/j-default-char-type-is-unsigned.md)-Compileroption ändert den Standardtyp für **`char`** von **`signed char`** in **`unsigned char`** .

## <a name="see-also"></a>Siehe auch

[Zeichen](../c-language/characters.md)
