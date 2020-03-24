---
title: Schwerwiegender Fehler C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204931"
---
# <a name="fatal-error-c1002"></a>Schwerwiegender Fehler C1002

Im 2. Durchlauf ist kein Heapspeicher mehr für den Compiler verfügbar.

Der Compiler hat während des zweiten Durchlauf nicht den dynamischen Arbeitsspeicher Bereich verursacht, wahrscheinlich aufgrund eines Programms mit zu vielen Symbolen oder komplexen Ausdrücken.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Unterteilen Sie die Quelldatei in mehrere kleinere Dateien.

1. Unterbrechen Sie Ausdrücke in kleinere Teil Ausdrücke.

1. Entfernen Sie andere Programme oder Treiber, die Arbeitsspeicher belegen.
