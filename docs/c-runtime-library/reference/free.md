---
title: frei
ms.date: 4/2/2020
api_name:
- free
- _o_free
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345976"
---
# <a name="free"></a>frei

Hebt die Zuweisung eines Speicherblocks auf oder gibt diesen frei.

## <a name="syntax"></a>Syntax

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parameter

*memblock*<br/>
Zuvor zugewiesener Speicherblock, der freigegeben werden soll.

## <a name="remarks"></a>Bemerkungen

Die **freie** Funktion weist einen Speicherblock (*memblock*) auf, der zuvor durch einen Aufruf von **calloc**, **malloc**oder **realloc**zugewiesen wurde. Die Anzahl der freigegebenen Bytes entspricht der Anzahl der Bytes, die beim Zuweisen des Blocks angefordert wurden (oder im Fall von **realloc)** umverteilt wurden. Wenn *memblock* **NULL**ist, wird der Zeiger ignoriert und **free** kehrt sofort zurück. Der Versuch, einen ungültigen Zeiger freizugeben (ein Zeiger auf einen Speicherblock, der nicht von **calloc**, **malloc**oder **realloc**zugewiesen wurde), kann sich auf nachfolgende Zuweisungsanforderungen auswirken und Fehler verursachen.

Wenn beim Freilassen des Speichers ein Fehler auftritt, wird **errno** mit Informationen des Betriebssystems über die Art des Fehlers festgelegt. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Nachdem ein Speicherblock freigegeben wurde, minimiert [_heapmin](heapmin.md) die Menge des freien Speicherplatzes auf dem Heap, indem die nicht verwendeten Bereiche zusammengefügt und wieder an das Betriebssystem freigegeben werden. Freigegebener Speicher, der nicht an das Betriebssystem freigegeben wird, wird im freien Pool wiederhergestellt und ist wieder für eine Zuordnung verfügbar.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **die kostenlose** Auflösung [in _free_dbg](free-dbg.md). Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**frei** ist `__declspec(noalias)`markiert, was bedeutet, dass die Funktion garantiert keine globalen Variablen ändert. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md).

Um Speicher mit [_malloca](malloca.md) freizugeben, verwenden Sie [_freea](freea.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**kostenlos**|\<stdlib.h> und \<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [malloc](malloc.md).

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
