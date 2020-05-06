---
title: Speicherung von Bitfeldern
ms.date: 11/04/2016
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
ms.openlocfilehash: 4dbfb3c6ad27fb023881dafde74bb27132959085
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157882"
---
# <a name="storage-of-bit-fields"></a>Speicherung von Bitfeldern

**ANSI 3.5.2.1** Die Reihenfolge der Zuordnung von Bitfeldern in einem „int“

Bitfelder werden innerhalb einer Ganzzahl vom niedrigstwertigen hin zum höchstwertigen Bit angeordnet. Im folgenden Code etwa

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

wären die Bits folgendermaßen angeordnet:

```
00000001 11110010
cccccccb bbbbaaaa
```

Da die 80x86-Prozessoren das niedrige Byte ganzzahliger Werte vor dem hohen Byte speichern, wird die oben stehende Ganzzahl 0x01F2 im physischen Speicher als 0xF2 gefolgt von 0x01 gespeichert.

## <a name="see-also"></a>Siehe auch

[Strukturen, Unions, Enumerationen und Bitfelder](../c-language/structures-unions-enumerations-and-bit-fields.md)
