---
title: Speicherzuweisung
ms.date: 11/18/2020
description: Liste der Microsoft C-Lauf Zeitfunktionen, die zum zuordnen, freigeben und erneuten Zuweisen von Arbeitsspeicher verwendet werden.
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.openlocfilehash: 39be48a4ebdf8ee917395d7b743846196200878d
ms.sourcegitcommit: e82e13b80150fcb27a1387018aafb00d99a3827a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94920741"
---
# <a name="memory-allocation"></a>Arbeitsspeicherbelegung

Diese Routinen ordnen Speicher frei und ordnen ihn neu zu.

## <a name="memory-allocation-routines"></a>Speicher Belegungs Routinen

|-Routine zurückgegebener Wert|Verwendung|
|-------------|---------|
|[`_alloca`](../c-runtime-library/reference/alloca.md), [`_malloca`](../c-runtime-library/reference/malloca.md)|Arbeitsspeicher aus dem Stapel zuweisen|
|[`calloc`](../c-runtime-library/reference/calloc.md)|Ein Array zuordnen und seine Elemente auf 0 (null) initialisieren|
|[`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md)|Debugversion von **`calloc`** . Nur in den Debugversionen der Laufzeitbibliotheken verfügbar.|
|[`operator delete`, `operator delete[]`](../c-runtime-library/delete-operator-crt.md)|Frei zugeordneter Arbeitsspeicher auf dem Heap |
|[`_expand`](../c-runtime-library/reference/expand.md)|Vergrößern oder Verkleinern eines Speicherblocks, ohne ihn zu verschieben|
|[`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md)|Debugversion von **`_expand`** . Nur in den Debugversionen der Laufzeitbibliotheken verfügbar.|
|[`free`](../c-runtime-library/reference/free.md)|Frei zugeordneter Arbeitsspeicher auf dem Heap|
|[`_free_dbg`](../c-runtime-library/reference/free-dbg.md)|Debugversion von **`free`** . Nur in den Debugversionen der Laufzeitbibliotheken verfügbar.|
|[`_freea`](../c-runtime-library/reference/freea.md)|Auf dem Stapel zugeordneter freier Speicher|
|[`_get_heap_handle`](../c-runtime-library/reference/get-heap-handle.md)|Eine Win32-Datei `HANDLE` zum C-Lauf Zeit Heap (CRT).|
|[`_heapadd`](../c-runtime-library/heapadd.md)|Hinzufügen von Arbeitsspeicher zum Heap|
|[`_heapchk`](../c-runtime-library/reference/heapchk.md)|Überprüfen des Heaps auf Konsistenz|
|[`_heapmin`](../c-runtime-library/reference/heapmin.md)|Freigeben von nicht genutztem Speicher im Heap|
|[`_heapset`](../c-runtime-library/heapset.md)|Auffüllen von freien Heap Einträgen mit einem Wert|
|[`_heapwalk`](../c-runtime-library/reference/heapwalk.md)|Informationen zu jedem Eintrag im Heap erhalten|
|[`malloc`](../c-runtime-library/reference/malloc.md)|Zuweisen von Arbeitsspeicher aus dem Heap|
|[`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md)|Debugversion von **`malloc`** ; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[`_msize`](../c-runtime-library/reference/msize.md)|Gibt die Größe eines zugeordneten Speicherblocks zurück.|
|[`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md)|Debugversion von **`_msize`** ; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[`new`, `new[]`](../c-runtime-library/new-operator-crt.md)|Zuordnen eines Speicherblocks aus dem Heap|
|[`_query_new_handler`](../c-runtime-library/reference/query-new-handler.md)|Gibt die Adresse der aktuellen neuen Handlerroutine an, festgelegt von **`_set_new_handler`**|
|[`_query_new_mode`](../c-runtime-library/reference/query-new-mode.md)|Den neuen handlermodus, der von festgelegt wird, **`_set_new_mode`****`malloc`**|
|[`realloc`](../c-runtime-library/reference/realloc.md)|Neuzuordnen eines Blocks zu einer neuen Größe|
|[`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md)|Debugversion von **`realloc`** ; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md)|Aktivieren Sie den Fehler Behandlungs Mechanismus, wenn der **`new`** Operator keinen Arbeitsspeicher zuordnen kann, und aktivieren Sie die Kompilierung der C++-Standard Bibliotheken.|
|[`_set_new_mode`](../c-runtime-library/reference/set-new-mode.md)|Legen Sie den neuen handlermodus für fest. **`malloc`**|

## <a name="see-also"></a>Weitere Informationen:

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)