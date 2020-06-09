---
title: 'Speicherverwaltung: Größenveränderbare Speicherblöcke'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626271"
---
# <a name="memory-management-resizable-memory-blocks"></a>Speicherverwaltung: Größenveränderbare Speicherblöcke

Die **New** -und **Delete** -Operatoren, die im Artikel [Speicherverwaltung: Beispiele](memory-management-examples.md)beschrieben werden, eignen sich gut für die Zuordnung und Aufhebung der Zuordnung von Speicherblöcken und Objekten fester Größe. Gelegentlich benötigt Ihre Anwendung möglicherweise in der Größe verwertbare Speicherblöcke. Sie müssen die standardmäßigen C-Lauf Zeit Bibliotheksfunktionen " [malloc](../c-runtime-library/reference/malloc.md)", " [rebelegc](../c-runtime-library/reference/realloc.md)" und " [Free](../c-runtime-library/reference/free.md) " verwenden, um die Größe der Größe von Speicherblöcken auf dem Heap zu verwalten

> [!IMPORTANT]
> Das Kombinieren der **New** -und **Delete** -Operatoren mit den Größenänderung der Speicher Belegungs Funktion im gleichen Speicherblock führt zu einem beschädigten Arbeitsspeicher in der Debugversion von MFC. Sie sollten **rezuzuweisungen** nicht für einen Speicherblock verwenden, der mit **New**zugeordnet ist. Ebenso sollten Sie dem **New** -Operator keinen Speicherblock zuordnen und ihn mit " **Free**" löschen oder den **Delete** -Operator für einen Speicherblock verwenden, der mit **malloc**zugeordnet ist.

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung: Heapbelegung](memory-management-heap-allocation.md)
