---
title: Umwandlung ganzer Zahlen in Gleitkommazahlen-Punktwerte
ms.date: 11/04/2016
helpviewer_keywords:
- integers, casting to floating-point values
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
ms.openlocfilehash: b3c65beee0cef4eb74d1bad3c03e5a9c11efae27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227919"
---
# <a name="casting-integers-to-floating-point-values"></a>Umwandlung ganzer Zahlen in Gleitkommazahlen-Punktwerte

**ANSI 3.2.1.3** Die Richtung des Abschneidens, wenn eine Ganzzahl in eine Gleitkommazahl konvertiert wird, die den ursprünglichen Wert nicht genau darstellen kann.

Wenn eine Ganzzahl in einen Gleitkommawert umgewandelt wird, der den Wert nicht genau darstellen kann, wird der Wert auf den geeigneten nächsten Wert auf- oder abgerundet.

Zum Beispiel wird beim Umwandeln eines **`unsigned long`** -Werts (mit 32 Bits Genauigkeit) in einen **`float`** -Wert (dessen Mantisse 23 Bits Genauigkeit hat) die Zahl auf das nächste Vielfache von 256 gerundet. Die **`long`** -Werte 4.294.966.913 bis 4.294.967.167 werden alle auf den **`float`** -Wert 4.294.967.040 abgerundet.

## <a name="see-also"></a>Siehe auch

[Gleitkommaoperationen](../c-language/floating-point-math.md)
