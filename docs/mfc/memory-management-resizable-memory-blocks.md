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
ms.openlocfilehash: 308b5aa00aeb1f0e7887ad90bad79a28b361d7c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217921"
---
# <a name="memory-management-resizable-memory-blocks"></a>Speicherverwaltung: Größenveränderbare Speicherblöcke

Die **`new`** **`delete`** Operatoren und, die im Artikel [Speicherverwaltung: Beispiele](memory-management-examples.md)beschrieben werden, eignen sich gut für die Zuordnung und Aufhebung der Zuordnung von Speicherblöcken und Objekten fester Größe. Gelegentlich benötigt Ihre Anwendung möglicherweise in der Größe verwertbare Speicherblöcke. Sie müssen die standardmäßigen C-Lauf Zeit Bibliotheksfunktionen " [malloc](../c-runtime-library/reference/malloc.md)", " [rebelegc](../c-runtime-library/reference/realloc.md)" und " [Free](../c-runtime-library/reference/free.md) " verwenden, um die Größe der Größe von Speicherblöcken auf dem Heap zu verwalten

> [!IMPORTANT]
> Das Kombinieren der **`new`** **`delete`** Operatoren und mit den in der Größe zu ändern Speicher Belegungs Funktionen für denselben Speicherblock führt zu einem beschädigten Speicher in der Debugversion von MFC. Sie sollten **rezuzuweisungen** nicht für einen Speicherblock verwenden, der zugeordnet ist **`new`** . Ebenso sollten Sie dem Operator keinen Speicherblock zuordnen **`new`** und ihn mit " **Free**" löschen oder den **`delete`** Operator für einen mit **malloc**zugeordneten Speicherblock verwenden.

## <a name="see-also"></a>Weitere Informationen

[Speicherverwaltung: Heap Zuordnung](memory-management-heap-allocation.md)
