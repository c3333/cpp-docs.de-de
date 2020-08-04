---
title: Speicherung und Ausrichtung von Strukturen
ms.date: 11/04/2016
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
ms.openlocfilehash: 81f5b640585ec3b55e4e3d65b37ea0929a757473
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229479"
---
# <a name="storage-and-alignment-of-structures"></a>Speicherung und Ausrichtung von Strukturen

**Microsoft-spezifisch**

Strukturmember werden nacheinander in der Reihenfolge gespeichert, in der sie deklariert werden: das erste Member hat die niedrigste Speicheradresse und das letzte Member die höchste.

Jedes Datenobjekt verfügt über ein *alignment-requirement*. Für eine Struktur ist die Anforderung das größte seiner Member. Jedem Objekt wird ein *offset* zugeordnet, sodass Folgendes gilt:

*Offset* `%` *Ausrichtungsanforderung* `==` 0

Benachbarte Bitfelder sind in derselben 1-, 2- oder 4-Byte-Speicherbelegungseinheit gepackt, wenn die Ganzzahltypen die gleiche Größe aufweisen und das folgende Bitfeld in die aktuelle Speicherbelegungseinheit passt, ohne die Grenze zu überschreiten, die durch die allgemeinen Ausrichtungsanforderungen der Bitfelder auferlegt werden.

Um Speicherplatz zu sparen und vorhandene Datenstrukturen nicht zu überschreiten, können Sie Strukturen relativ kompakt speichern. Die [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*]-Compileroption sowie [#pragma pack](../preprocessor/pack.md) steuern, wie Strukturdaten im Speicher gepackt werden. Wenn Sie die Option „/Zp[*n*]“ verwenden, und *n* gleich 1, 2, 4, 8 oder 16 ist, werden die einzelnen Strukturmember nach dem ersten auf Byte-Begrenzungen gespeichert, die die Ausrichtungsanforderung des Felds oder die Komprimierungsgröße darstellen (*n*), je nachdem, welche kleiner ist. Ausgedrückt als Formel, sind die Bytegrenzen

```
min( n, sizeof( item ) )
```

wobei *n* die Komprimierungsgröße ist, ausgedrückt mit der /Zp[*n*]-Option, und *item* ist der Strukturmember. Die Standardkomprimierungsgröße ist "/Zp8".

Um mit dem `pack`-Pragma eine andere Komprimierung als die in der Befehlszeile für eine bestimmte Struktur angegebene festzulegen, geben Sie das `pack`-Pragma, bei dem die Komprimierungsgröße 1, 2, 4, 8 oder 16 ist, vor der Struktur an. Um die an der Befehlszeile angegebene Komprimierung wiederherzustellen, geben Sie das `pack`-Pragma ohne Argumente an.

Bitfelder verwenden für den Microsoft-C-Compiler standardmäßig die Größe **`long`** . Strukturmember werden nach der Größe des Typs oder der /Zp [*n*]-Größe ausgerichtet, je nachdem, welche kleiner ist. Die Standardgröße ist 4.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Strukturdeklarationen](../c-language/structure-declarations.md)
