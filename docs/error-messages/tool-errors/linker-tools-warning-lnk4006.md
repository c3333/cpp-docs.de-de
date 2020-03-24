---
title: Linkertoolwarnung LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194316"
---
# <a name="linker-tools-warning-lnk4006"></a>Linkertoolwarnung LNK4006

das Symbol ist bereits im Objekt definiert. zweite Definition wird ignoriert.

Das gegebene `symbol`, angezeigt in seiner ergänzten Form, wurde mehrfach definiert. Wenn diese Warnung auftritt, wird `symbol` zweimal hinzugefügt, es wird jedoch nur das erste Formular verwendet.

Sie können diese Warnung erhalten, wenn Sie versuchen, zwei Import Bibliotheken in einer zusammenzuführen.

Wenn Sie die C-Lauf Zeit Bibliothek neu erstellen, können Sie diese Meldung ignorieren.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Der angegebene `symbol` kann eine Paket Funktion sein, die durch Kompilieren mit [/Gy](../../build/reference/gy-enable-function-level-linking.md)erstellt wird. Dieses Symbol war in mehr als einer Datei enthalten, wurde jedoch zwischen Kompilierungen geändert. Kompilieren Sie alle Dateien neu, die die `symbol`enthalten.

1. Der angegebene `symbol` wurde möglicherweise in zwei Member-Objekten in verschiedenen Bibliotheken anders definiert.

1. Ein absoluter Wert wurde möglicherweise zweimal mit einem anderen Wert in jeder Definition definiert.

1. Wenn die Fehlermeldung beim Kombinieren von Bibliotheken empfangen wird, ist `symbol` bereits in der Bibliothek vorhanden, der hinzugefügt wird.
