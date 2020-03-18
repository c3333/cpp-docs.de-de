---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438883"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Bemerkungen

Mit dieser Option wird die Größe des Stapels in Byte festgelegt, und es werden Argumente in der Dezimal-oder C-Sprache festgelegt. Die/Stack-Option gilt nur für eine ausführbare Datei.

Das *Reserve* Argument gibt die gesamte Stapel Zuordnung im virtuellen Speicher an. EDITBIN rundet den angegebenen Wert auf die nächsten 4 Bytes auf.

Das optionale `commit`-Argument unterliegt der Interpretation durch das Betriebssystem. In Windows NT, Windows 95 und Windows 98 gibt `commit` die Menge des physischen Speichers an, der gleichzeitig belegt werden soll. Die Zusicherung von virtuellem Speicher bewirkt die Belegung von Speicher in der Auslagerungsdatei. Ein höherer `commit` Wert spart Zeit, wenn die Anwendung mehr Stapel Speicher benötigt, aber die Arbeitsspeicher Anforderungen und möglicherweise die Startzeit erhöht.

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)
