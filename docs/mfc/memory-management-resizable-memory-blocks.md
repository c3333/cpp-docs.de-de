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
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364772"
---
# <a name="memory-management-resizable-memory-blocks"></a>Speicherverwaltung: Größenveränderbare Speicherblöcke

Die **neuen** und löschen-Operatoren, die im Artikel **delete** [Speicherverwaltung: Beispiele](../mfc/memory-management-examples.md)beschrieben werden, eignen sich zum Zuweisen und Verteilen von Speicherblöcken und Objekten fester Größe. Gelegentlich benötigt Ihre Anwendung möglicherweise speicherbare Speicherblöcke in der geänderten Datei. Sie müssen die standardmäßigen C-Laufzeitbibliotheksfunktionen [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)und [free](../c-runtime-library/reference/free.md) verwenden, um könnende Speicherblöcke auf dem Heap verwalten.

> [!IMPORTANT]
> Das Mischen der **neuen** und **löschbaren** Operatoren mit den funktionen für die Speicherzuweisung in der geänderten Speicherzuweisung auf demselben Speicherblock führt zu beschädigtem Speicher in der Debugversion von MFC. Sie sollten **realloc** nicht für einen Speicherblock verwenden, der mit **new**zugeordnet ist. Ebenso sollten Sie keinen Speicherblock mit dem **neuen** Operator zuweisen und ihn mit **free**löschen oder den **delete-Operator** auf einem Speicherblock verwenden, der mit **malloc**zugeordnet ist.

## <a name="see-also"></a>Siehe auch

[Speicherverwaltung: Heapbelegung](../mfc/memory-management-heap-allocation.md)
