---
title: Ausdrucksauswertung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233846"
---
# <a name="expression-evaluation-c"></a>Ausdrucksauswertung (C)

Ausdrücke, die mit Zuweisung, unärem Inkrement bzw. unärem Dekrement zusammenhängen oder eine Funktion aufrufen, können Folgen haben, die mit ihrer Auswertung auftreten (Nebeneffekte). Mit dem Erreichen eines "Sequenzpunkts" wird gewährleistet, dass alles vor dem Sequenzpunkt, einschließlich aller möglichen Nebeneffekte, ausgewertet wurde, bevor die Auswertung von Elementen nach dem Sequenzpunkt fortgesetzt wird.

"Nebeneffekte" sind die Änderungen, die durch die Auswertung eines Ausdrucks verursacht werden. Nebeneffekte treten auf, wenn der Wert einer Variablen durch eine Ausdrucksauswertung geändert wird. Alle Zuweisungsvorgänge haben Nebeneffekte. Funktionsaufrufe können auch Nebeneffekte haben, wenn sie den Wert eines extern sichtbaren Elements entweder durch direkte oder indirekte Zuweisung über einen Zeiger ändern.

## <a name="see-also"></a>Siehe auch

[Operanden und Ausdrücke](../c-language/operands-and-expressions.md)
