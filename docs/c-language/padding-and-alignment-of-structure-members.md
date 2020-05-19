---
title: Abstand und Ausrichtung von Strukturmembern
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325356"
---
# <a name="padding-and-alignment-of-structure-members"></a>Abstand und Ausrichtung von Strukturmembern

**ANSI 3.5.2.1** Der Abstand und die Ausrichtung von Strukturmembern und die Angabe, ob ein Bitfeld eine Speichereinheitsgrenze umspannen kann

Strukturmember werden nacheinander in der Reihenfolge gespeichert, in der sie deklariert werden: das erste Member hat die niedrigste Speicheradresse und das letzte Member die höchste.

Jedes Datenobjekt verfügt über ein alignment-requirement. Das alignment-requirement für alle Daten (außer Strukturen, Unions und Arrays) ist entweder die Größe des Objekts oder die aktuelle Komprimierungsgröße (diese wird entweder mit "/Zp" oder dem `pack`-Pragma angegeben, je nachdem, was kleiner ist). Bei Strukturen, Unions und Arrays ist das alignment-requirement die größte Ausrichtungsanforderung ihrer Member. Jedem Objekt wird ein offset zugeordnet, sodass Folgendes gilt:

*offset* **%** *alignment-requirement* **== 0**

Benachbarte Bitfelder sind in derselben 1-, 2- oder 4-Byte-Speicherbelegungseinheit gepackt, wenn die Ganzzahltypen die gleiche Größe aufweisen und das folgende Bitfeld in die aktuelle Speicherbelegungseinheit passt, ohne die Grenze zu überschreiten, die durch die allgemeinen Ausrichtungsanforderungen der Bitfelder auferlegt werden.

## <a name="see-also"></a>Siehe auch

[Strukturen, Unions, Enumerationen und Bitfelder](../c-language/structures-unions-enumerations-and-bit-fields.md)
