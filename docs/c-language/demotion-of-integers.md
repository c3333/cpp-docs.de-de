---
title: Degradierung von Ganzzahlen
ms.date: 11/04/2016
helpviewer_keywords:
- demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
ms.openlocfilehash: aee0a5041cd37b1fbad785b760b8cefde74eb195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218883"
---
# <a name="demotion-of-integers"></a>Degradierung von Ganzzahlen

**ANSI 3.2.1.2** Das Ergebnis der Konvertierung einer ganzen Zahl in eine kürzere Ganzzahl mit Vorzeichen oder das Ergebnis der Konvertierung einer Ganzzahl ohne Vorzeichen in eine Ganzzahl mit Vorzeichen derselben Länge, wenn der Wert nicht dargestellt werden kann

Wenn eine ganze Zahl vom Typ **`long`** in den Typ **`short`** oder vom Typ **`short`** in den Typ **`char`** umgewandelt wird, werden die unwichtigsten Bytes beibehalten.

Diese Zeile weist beispielsweise

```
short x = (short)0x12345678L;
```

`x` den Wert 0x5678 zu, und diese Zeile

```
char y = (char)0x1234;
```

weist `y` den Wert 0x34 zu.

Wenn Variablen vom Typ **`signed`** in Variablen vom Typ **`unsigned`** und umgekehrt konvertiert werden, bleiben die Bitmuster identisch. Zum Beispiel ergibt die Umwandlung von -2 (0xFE) in einen **`unsigned`** -Wert 254 (auch 0xFE).

## <a name="see-also"></a>Siehe auch

[Ganze Zahlen](../c-language/integers.md)
