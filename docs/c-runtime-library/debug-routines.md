---
title: Debugroutinen
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: 59e705947856ba9fe9477e88328b1fb2344abb7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842493"
---
# <a name="debug-routines"></a>Debugroutinen

Die Debugversion der C-Laufzeitbibliothek stellt viele Diagnosedienste bereit, die das Debuggen von Programmen vereinfachen und Entwicklern Folgendes ermöglichen:

- Ausführen von einzelnen Schritten direkt in die Laufzeitfunktionen während des Debuggens

- Beheben von Assertionen, Fehlern und Ausnahmen

- Nachverfolgen von Heapzuordnungen und Verhindern von Speicherverlusten

- Übermitteln von Debugmeldungen an den Benutzer

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Debugversionen der C-Laufzeitbibliotheksroutinen

Um diese Routinen zu verwenden, muss das [_DEBUG](../c-runtime-library/debug.md)-Flag definiert werden. Alle diese Routinen führen in einer Verkaufsversion einer Anwendung keine Aktionen aus. Weitere Informationen zur Verwendung der neuen Debugroutinen finden Sie unter [CRT Debugging Techniques (CRT-Debugverfahren)](/visualstudio/debugger/crt-debugging-techniques).

| -Routine zurückgegebener Wert | Verwendung |
|--|--|
| [`_ASSERT`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | Wertet einen Ausdruck aus und erzeugt einen Debugbericht, wenn das Ergebnis "FALSE" lautet. |
| [`_ASSERTE`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | Ähnlich wie **`_ASSERT`** , schließt jedoch den fehlgeschlagenen Ausdruck im generierten Bericht ein. |
| [`_CrtCheckMemory`](../c-runtime-library/reference/crtcheckmemory.md) | Bestätigt die Integrität der Speicherblöcke, die im Debugheap zugeordnet werden. |
| [`_CrtDbgBreak`](../c-runtime-library/reference/crtdbgbreak.md) | Legt einen Haltepunkt fest. |
| [`_CrtDbgReport`, `_CrtDbgReportW`](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) | Generiert einen Debugbericht mit einer Benutzermeldung und sendet den Bericht an drei mögliche Ziele. |
| [`_CrtDoForAllClientObjects`](../c-runtime-library/reference/crtdoforallclientobjects.md) | Ruft eine von der Anwendung bereitgestellte Funktion für alle `_CLIENT_BLOCK`-Typen auf dem Heap auf. |
| [`_CrtDumpMemoryLeaks`](../c-runtime-library/reference/crtdumpmemoryleaks.md) | Gibt alle Speicherblöcke im Debugheap aus, wenn ein bedeutender Speicherverlust aufgetreten ist. |
| [`_CrtIsMemoryBlock`](../c-runtime-library/reference/crtismemoryblock.md) | Überprüft, ob sich ein angegebener Speicherblock im lokalen Heap befindet und ob er einen gültigen Debugheap-Blocktypbezeichner hat. |
| [`_CrtIsValidHeapPointer`](../c-runtime-library/reference/crtisvalidheappointer.md) | Überprüft, ob sich ein angegebener Zeiger im lokalen Heap befindet. |
| [`_CrtIsValidPointer`](../c-runtime-library/reference/crtisvalidpointer.md) | Überprüft, ob ein bestimmter Speicherbereich für Lese- und Schreibvorgänge gültig ist. |
| [`_CrtMemCheckpoint`](../c-runtime-library/reference/crtmemcheckpoint.md) | Ruft den aktuellen Zustand des Debugheaps ab und speichert ihn in einer von der Anwendung bereitgestellten `_CrtMemState`-Struktur. |
| [`_CrtMemDifference`](../c-runtime-library/reference/crtmemdifference.md) | Vergleicht zwei Speicherzustände für wesentliche Unterschiede und gibt die Ergebnisse zurück. |
| [`_CrtMemDumpAllObjectsSince`](../c-runtime-library/reference/crtmemdumpallobjectssince.md) | Gibt Informationen über Objekte auf dem Heap aus, seit ein angegebener Prüfpunkt übernommen wurde oder ab Beginn der Programmausführung. |
| [`_CrtMemDumpStatistics`](../c-runtime-library/reference/crtmemdumpstatistics.md) | Gibt die Debugheaderinformationen für einen angegebenen Speicherzustand in einer für den Benutzer lesbaren Form aus. |
| [`_CrtReportBlockType`](../c-runtime-library/reference/crtreportblocktype.md) | Gibt den Blocktyp/den Untertyp zurück, der einem angegebenen Debugheapblockzeiger zugeordnet ist. |
| [`_CrtSetAllocHook`](../c-runtime-library/reference/crtsetallochook.md) | Installiert eine clientdefinierte Zuordnungsfunktion, indem sie mit dem Debug-Speicherbelegungsprozess der C-Laufzeit verknüpft wird. |
| [`_CrtSetBreakAlloc`](../c-runtime-library/reference/crtsetbreakalloc.md) | Legt einen Haltepunkt an einer angegebenen Befehlsnummer der Objektzuordnung fest. |
| [`_CrtSetDbgFlag`](../c-runtime-library/reference/crtsetdbgflag.md) | Ruft den Zustand des `_crtDbgFlag`-Flags ab oder ändert ihn, um das Zuordnungsverhalten des Debugheapmanagers zu steuern. |
| [`_CrtSetDumpClient`](../c-runtime-library/reference/crtsetdumpclient.md) | Installiert eine anwendungsdefinierte Funktion, die bei jedem Aufruf einer Debugdumpfunktion aufgerufen wird, um `_CLIENT_BLOCK`-Typspeicherblöcke auszugeben. |
| [`_CrtSetReportFile`](../c-runtime-library/reference/crtsetreportfile.md) | Identifiziert die als Ziel für einen bestimmten Berichtstyp von `_CrtDbgReport` zu verwendende Datei bzw. Stream. |
| [`_CrtSetReportHook`](../c-runtime-library/reference/crtsetreporthook.md) | Installiert eine clientdefinierte Berichtsfunktion, indem sie mit dem Debug-Berichterstellungsprozess der C-Laufzeit verknüpft wird. |
| [`_CrtSetReportHook2`, `_CrtSetReportHookW2`](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) | Installiert bzw. deinstalliert eine clientdefinierte Berichtsfunktion, indem sie mit dem Debug-Berichterstellungsprozess der C-Laufzeit verknüpft wird. |
| [`_CrtSetReportMode`](../c-runtime-library/reference/crtsetreportmode.md) | Gibt die allgemeinen Ziele für einen bestimmten Berichtstyp an, der von `_CrtDbgReport` generiert wird. |
| [_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | Verfolgt den Status der Anwendung durch Generieren eines Debugberichts, indem `_CrtDbgReport` mit einer Formatzeichenfolge und einer variablen Anzahl von Argumenten aufgerufen wird. Stellt keine Quelldatei und Zeilennummern bereit. |
| [_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | Ähnlich den `_RPTn`-Makros, jedoch werden der Quelldateiname und die Zeilennummer bereitgestellt, aus denen die Berichtsanforderung stammt. |
| [`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md) | Ordnet eine bestimmte Anzahl von Speicherblöcken auf dem Heap mit zusätzlichem Speicher für einen Debugheader und Überschreibungspuffer zu. |
| [`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md) | Ändert die Größe eines angegebenen Speicherblocks auf dem Heap, indem der Block erweitert oder verkleinert wird. |
| [`_free_dbg`](../c-runtime-library/reference/free-dbg.md) | Gibt einen Speicherblock auf dem Heap frei. |
| [`_fullpath_dbg`, `_wfullpath_dbg`](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md) | Erstellen Sie einen absoluten oder vollständigen Pfadnamen für den angegebenen relativen Pfadnamen, und verwenden Sie [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) zum Zuordnen von Arbeitsspeicher. |
| [`_getcwd_dbg`, `_wgetcwd_dbg`](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md) | Sie können das aktuelle Arbeitsverzeichnis mithilfe [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) von zum Zuweisen von Arbeitsspeicher erhalten. |
| [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) | Ordnet einen Speicherblock auf dem Heap mit zusätzlichem Speicher für einen Debugheader und Überschreibungspuffer zu. |
| [`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md) | Berechnet die Größe eines Speicherblocks auf dem Heap. |
| [`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md) | Ordnet einen angegebenen Speicherblock auf dem Heap neu zu, indem der Block verschoben und/oder seine Größe geändert wird. |
| [`_strdup_dbg`, `_wcsdup_dbg`](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md) | Dupliziert eine Zeichenfolge, indem verwendet wird, [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) um Arbeitsspeicher zuzuweisen. |
| [`_tempnam_dbg`, `_wtempnam_dbg`](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) | Generieren Sie Namen, mit denen Sie temporäre Dateien erstellen können, indem Sie verwenden, [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) um Speicher zuzuweisen. |

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>C-Laufzeitroutinen, die nicht im Quellcodeformat verfügbar sind

Der Debugger kann verwendet werden, um den Quellcode für die meisten C-Laufzeitroutinen während des Debugprozesses schrittweise auszuführen. Allerdings erachtet Microsoft einige Technologien als proprietär und stellt daher keinen Quellcode für einen Teil dieser Routinen bereit. Die meisten dieser Routinen gehören zur Ausnahmebehandlung oder zu den Gruppen der Gleitkommaverarbeitung, einige andere werden jedoch ebenfalls eingeschlossen. In der folgenden Tabelle sind diese Routinen aufgeführt.

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`acosh`](../c-runtime-library/reference/acosh-acoshf-acoshl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
      [`asinh`](../c-runtime-library/reference/asinh-asinhf-asinhl.md)\
      [`atan`, `atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atanh`](../c-runtime-library/reference/atanh-atanhf-atanhl.md)\
      [`Bessel functions`](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)\
      [`_cabs`](../c-runtime-library/reference/cabs.md)\
      [`ceil`](../c-runtime-library/reference/ceil-ceilf-ceill.md)\
      [`_chgsign`](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)\
      [`_clear87`, `_clearfp`](../c-runtime-library/reference/clear87-clearfp.md)\
      [`_control87`, `_controlfp`](../c-runtime-library/reference/control87-controlfp-control87-2.md)
   :::column-end:::
   :::column span="":::
      [`copysign`](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`Exp`](../c-runtime-library/reference/exp-expf.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_finite`](../c-runtime-library/reference/finite-finitef.md)\
      [`floor`](../c-runtime-library/reference/floor-floorf-floorl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
      [`_fpclass`](../c-runtime-library/reference/fpclass-fpclassf.md)\
      [`_fpieee_flt`](../c-runtime-library/reference/fpieee-flt.md)\
      [`_fpreset`](../c-runtime-library/reference/fpreset.md)\
      [`frexp`](../c-runtime-library/reference/frexp.md)
   :::column-end:::
   :::column span="":::
      [`_hypot`](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)\
      [`_isnan`](../c-runtime-library/reference/isnan-isnan-isnanf.md)\
      [`ldexp`](../c-runtime-library/reference/ldexp.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`_logb`](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)\
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`longjmp`](../c-runtime-library/reference/longjmp.md)\
      [`_matherr`](../c-runtime-library/reference/matherr.md)\
      [`modf`](../c-runtime-library/reference/modf-modff-modfl.md)\
      [`_nextafter`](../c-runtime-library/reference/nextafter-functions.md)\
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`printf_s`](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)
   :::column-end:::
   :::column span="":::
      [`printf`](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\
      [`_scalb`](../c-runtime-library/reference/scalb.md)\
      [`scanf_s`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\
      [`scanf`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)\
      [`setjmp`](../c-runtime-library/reference/setjmp.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`_status87`, `_statusfp`](../c-runtime-library/reference/status87-statusfp-statusfp2.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)
   :::column-end:::
:::row-end:::

Obwohl Quellcode für die meisten dieser **printf**- und **scanf**-Routinen verfügbar ist, rufen sie intern eine andere Routine auf, für die kein Quellcode bereitgestellt wird.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Routinen, die sich in einem Debugbuild einer Anwendung unterschiedlich verhalten

Einige C-Laufzeitfunktionen und C++-Operatoren verhalten sich unterschiedlich, wenn sie von einem Debugbuild einer Anwendung aufgerufen werden. (Beachten Sie, dass ein Debugbuild einer Anwendung ausgeführt werden kann, indem das-Flag definiert wird `_DEBUG` oder indem eine Verknüpfung mit einer Debugversion der C-Lauf Zeit Bibliothek erstellt wird.) Die Verhaltensunterschiede bestehen normalerweise aus zusätzlichen Features oder Informationen, die von der Routine zur Unterstützung des Debugprozesses bereitgestellt werden. In der folgenden Tabelle sind diese Routinen aufgeführt.

:::row:::
   :::column span="":::
      C- [`abort`](../c-runtime-library/reference/abort.md) Routine
   :::column-end:::
   :::column span="":::
      C- [`assert`](../c-runtime-library/reference/assert-macro-assert-wassert.md) Routine
   :::column-end:::
   :::column span="":::
      C++- [`delete`](../cpp/delete-operator-cpp.md) Operator
   :::column-end:::
   :::column span="":::
      C++- [`new`](../cpp/new-operator-cpp.md) Operator
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Laufzeitfehlerüberprüfung](../c-runtime-library/run-time-error-checking.md)<br/>
