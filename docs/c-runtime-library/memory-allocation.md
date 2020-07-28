---
title: Speicherzuweisung
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- memory allocation, routines
- memory, managing
- memory, allocation
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
ms.openlocfilehash: 2adfd0de21a5dc7a1f3aa65041a6b8a9a9cf1d69
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189505"
---
# <a name="memory-allocation"></a>Speicherzuweisung

Verwenden Sie diese Routinen zur Belegung, Freigabe und erneuten Belegung von Speicherplatz.

## <a name="memory-allocation-routines"></a>Speicherbelegungsroutinen

|-Routine zurückgegebener Wert|Zweck|
|-------------|---------|
|[_alloca](../c-runtime-library/reference/alloca.md), [_malloca](../c-runtime-library/reference/malloca.md)|Belegen von Speicher im Stapel|
|[calloc](../c-runtime-library/reference/calloc.md)|Belegen von Speicher für ein Array mit Initialisierung aller Bytes im belegten Block auf 0|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Debugversion von **calloc**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[Operator löschen](../c-runtime-library/operator-delete-crt.md)|Freigeben eines belegten Blocks|
|[operator delete&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|Freigeben eines belegten Blocks|
|[_expand](../c-runtime-library/reference/expand.md)|Erweitern oder Verkleinern eines Speicherblocks, ohne diesen zu bewegen|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Debugversion von **_expand**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[Kosten](../c-runtime-library/reference/free.md)|Freigeben eines belegten Blocks|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Debugversion von **free**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[_freea](../c-runtime-library/reference/freea.md)|Freigeben eines belegten Blocks aus dem Stapel|
|[_get_heap_handle](../c-runtime-library/reference/get-heap-handle.md)|Abrufen des Win32 HANDLEs aus dem CRT-Heap.|
|[_heapadd](../c-runtime-library/heapadd.md)|Hinzufügen von Speicher zum Heap.|
|[_heapchk](../c-runtime-library/reference/heapchk.md)|Prüfen des Heaps auf Konsistenz|
|[_heapmin](../c-runtime-library/reference/heapmin.md)|Freigeben von ungenutztem Speicher im Heap|
|[_heapset](../c-runtime-library/heapset.md)|Füllen freier Heap-Einträge mit bestimmten Werten|
|[_heapwalk](../c-runtime-library/reference/heapwalk.md)|Rückgabe von Informationen über jeden Eintrag im Heap|
|[malloc](../c-runtime-library/reference/malloc.md)|Belegen von Speicherblöcken aus dem Heap|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Debugversion von **malloc**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[_msize](../c-runtime-library/reference/msize.md)|Rückgabe der Größe des belegten Blocks|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Debugversion von **_msize**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[new](../c-runtime-library/operator-new-crt.md)|Belegen von Speicherblöcken aus dem Heap|
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|Belegen von Speicherblöcken aus dem Heap|
|[_query_new_handler](../c-runtime-library/reference/query-new-handler.md)|Zurückgeben der Adresse der aktuellen neuen Handlerroutine, wie in **_set_new_handler** festgelegt.|
|[_query_new_mode](../c-runtime-library/reference/query-new-mode.md)|Zurückgeben einer Ganzzahl, die den von **_set_new_mode** für **malloc** festgelegten neuen Handlermodus anzeigt.|
|[realloc](../c-runtime-library/reference/realloc.md)|Erneute Belegung eines Blocks zur neuen Größe|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Debugversion von **realloc**; nur in den Debugversionen der Laufzeitbibliotheken verfügbar|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|Aktivieren des Fehler Behandlungs Mechanismus, wenn der **`new`** Operator fehlschlägt (um Speicher zuzuweisen) und die Kompilierung von C++-Standard Bibliotheken aktivieren|
|[_set_new_mode](../c-runtime-library/reference/set-new-mode.md)|Festlegen eines neuen Handlermodus für **malloc**|

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
