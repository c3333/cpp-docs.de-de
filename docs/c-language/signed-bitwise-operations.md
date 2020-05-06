---
title: Signierte bitweise Operationen
ms.date: 11/04/2016
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
ms.openlocfilehash: 43f65fd5d1ea14ef5e15f18d9c8516ccf5fb1e08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158318"
---
# <a name="signed-bitwise-operations"></a>Signierte bitweise Operationen

**ANSI 3.3** Die Ergebnisse der bitweisen Vorgänge an Ganzzahlen mit Vorzeichen

Bitweise Vorgänge auf Ganzzahlen mit Vorzeichen arbeiten genauso wie bitweise Vorgänge auf Ganzzahlen ohne Vorzeichen. So kann beispielsweise `-16 & 99` binär ausgedrückt werden als

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Das Ergebnis des bitweisen AND-Vorgangs ist 96.

## <a name="see-also"></a>Siehe auch

[Ganze Zahlen](../c-language/integers.md)
