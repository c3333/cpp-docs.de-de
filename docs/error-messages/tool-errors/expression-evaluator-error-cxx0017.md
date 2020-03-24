---
title: Ausdrucksauswertungsfehler CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196013"
---
# <a name="expression-evaluator-error-cxx0017"></a>Ausdrucksauswertungsfehler CXX0017

Symbol wurde nicht gefunden.

Ein Symbol, das in einem Ausdruck angegeben wurde, wurde nicht gefunden.

Eine mögliche Ursache für diesen Fehler ist eine nicht übereinstimmende Groß-/Kleinschreibung im Symbolnamen. Da C und C++ Sprachen mit Unterscheidung nach Groß-/Kleinschreibung unterscheidet, muss ein Symbol Name in genau dem Fall angegeben werden, in dem er in der Quelle definiert ist.

Dieser Fehler kann auftreten, wenn Sie versuchen, eine Variable zu typisiert, um die Variable während des Debuggens anzuzeigen. Der `typedef` deklariert einen neuen Namen für einen Typ, aber keinen neuen Typ. Der Versuch der Typumwandlung im Debugger erfordert den Namen eines definierten Typs.

Dieser Fehler ist mit CAN0017 identisch.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Stellen Sie sicher, dass das Symbol bereits an dem Punkt im Programm deklariert ist, in dem es verwendet wird.

1. Verwenden Sie einen tatsächlichen Typnamen, um Variablen im Debugger anstelle eines `typedef`definierten Namens umzubenennen.
