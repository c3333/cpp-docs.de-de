---
title: 'Speicherverwaltung: Rahmenzuordnung'
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: cb66a0c0aea16f7e6831b6a1aff1a125df355210
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225045"
---
# <a name="memory-management-frame-allocation"></a>Speicherverwaltung: Rahmenzuordnung

Die Zuordnung im Frame übernimmt den Namen aus dem "Stapel Rahmen", der beim Aufruf einer Funktion eingerichtet wird. Der Stapel Rahmen ist ein Speicherbereich, der die Argumente für die Funktion und alle Variablen, die für die Funktion lokal definiert sind, vorübergehend enthält. Frame Variablen werden häufig als "automatische" Variablen bezeichnet, da der Compiler automatisch den Platz für diese Variablen zuordnet.

Es gibt zwei Hauptmerkmale von Frame Zuordnungen. Wenn Sie zunächst eine lokale Variable definieren, wird dem Stapel Rahmen genügend Speicherplatz zugeordnet, um die gesamte Variable zu speichern, auch wenn es sich um ein großes Array oder eine Datenstruktur handelt. Zweitens werden Frame Variablen automatisch gelöscht, wenn Sie den Gültigkeitsbereich verlassen:

[!code-cpp[NVC_MFC_Utilities#10](codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

Bei lokalen Funktions Variablen tritt dieser Bereichs Übergang auf, wenn die Funktion beendet wird, aber der Bereich einer Frame Variablen kann kleiner sein als eine Funktion, wenn die geschweiften Klammern verwendet werden. Das automatische Löschen von Frame Variablen ist äußerst wichtig. Bei einfachen primitiven Typen (z. b. **`int`** oder **Byte**), Arrays oder Datenstrukturen gibt der automatische Löschvorgang einfach den von der Variablen verwendeten Arbeitsspeicher frei. Da die Variable den Gültigkeitsbereich verlassen hat, kann auf Sie trotzdem nicht zugegriffen werden. Im Fall von C++-Objekten ist der Prozess der automatischen Löschung jedoch etwas komplizierter.

Wenn ein Objekt als Frame Variable definiert ist, wird der zugehörige Konstruktor automatisch an dem Punkt aufgerufen, an dem die Definition auftritt. Wenn das Objekt den Gültigkeitsbereich verlässt, wird der Dekonstruktor automatisch aufgerufen, bevor der Speicher für das Objekt freigegeben wird. Diese automatische Erstellung und Zerstörung kann sehr nützlich sein, aber Sie müssen die automatischen Aufrufe beachten, insbesondere für den Dekonstruktor.

Der Hauptvorteil der Zuordnung von Objekten im Frame besteht darin, dass Sie automatisch gelöscht werden. Wenn Sie die Objekte im Frame zuordnen, müssen Sie sich keine Gedanken über vergessene Objekte machen, die Speicher Verluste verursachen. (Ausführliche Informationen zu Speicher Verlusten finden Sie im Artikel [Erkennen von Speicher Verlusten in MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100)).) Ein Nachteil der Rahmen Zuordnung ist, dass Frame Variablen außerhalb ihres Bereichs nicht verwendet werden können. Ein weiterer Faktor bei der Auswahl von Frame Zuweisung und Heap Zuordnung ist, dass es bei großen Strukturen und Objekten häufig besser ist, den Heap anstelle des Stapels für den Speicher zu verwenden, da der Stapel Speicherplatz häufig eingeschränkt ist.

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung](memory-management.md)
