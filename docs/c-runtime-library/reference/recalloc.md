---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338121"
---
# <a name="_recalloc"></a>_recalloc

Eine Kombination aus **Realloc** und **calloc**. Ordnet ein Array im Speicher neu zu und initialisiert seine Elemente auf 0.

## <a name="syntax"></a>Syntax

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parameter

*memblock*<br/>
Zeiger zum vorherigen belegten Speicherblock.

*number*<br/>
Anzahl der Elemente.

*Größe*<br/>
Länge jedes Elements in Bytes.

## <a name="return-value"></a>Rückgabewert

**_recalloc** gibt einen **leeren** Zeiger auf den neu verteilten (und möglicherweise verschobenen) Speicherblock zurück.

Wenn nicht genügend Arbeitsspeicher verfügbar ist, um den Block auf die angegebene Größe zu erweitern, bleibt der ursprüngliche Block unverändert, und **NULL** wird zurückgegeben.

Wenn die angeforderte Größe Null ist, wird der Block, auf den *memblock* zeigt, freigegeben. Der Rückgabewert ist **NULL**, und *memblock* bleibt links und zeigt auf einen freigegebenen Block.

Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um einen Zeiger auf einen anderen Typ als **void**abzubekommen, verwenden Sie einen Typ, der für den Rückgabewert zurückgeworfen wird.

## <a name="remarks"></a>Bemerkungen

Die **_recalloc-Funktion** ändert die Größe eines zugewiesenen Speicherblocks. Das *memblock-Argument* zeigt auf den Anfang des Speicherblocks. Wenn *memblock* **NULL**ist, verhält **sich _recalloc** wie [calloc](calloc.md) und weist einen neuen Block von*Zahlengrößenbytes* *number* * zu. Jedes Element wird auf 0 initialisiert. Wenn *memblock* nicht **NULL**ist, sollte es sich um einen Zeiger handelt, der von einem vorherigen Aufruf von **calloc**, [malloc](malloc.md)oder [realloc](realloc.md)zurückgegeben wird.

Da sich der neue Block an einer neuen Speicherposition befinden kann, ist der von **_recalloc** zurückgegebene Zeiger nicht garantiert der Zeiger, der durch das *memblock-Argument* übergeben wird.

**_recalloc** setzt **errno** auf **ENOMEM,** wenn die Speicherzuweisung fehlschlägt oder wenn die angeforderte Speichermenge **_HEAP_MAXREQ**übersteigt. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** ruft **realloc** auf, um die C++-_set_new_mode-Funktion zum Festlegen des neuen Handlermodus zu verwenden. [_set_new_mode](set-new-mode.md) Der neue Handlermodus gibt an, ob **realloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **realloc** die neue Handlerroutine bei Nichtzuweisung von Arbeitsspeicher nicht auf. Sie können dieses Standardverhalten überschreiben, sodass **realloc** die neue Handlerroutine auf die gleiche Weise aufruft, wenn **_recalloc** Speicher nicht reserviert, wie der **neue** Operator, wenn er aus dem gleichen Grund ausfällt. Um den Standardwert zu überschreiben, rufen Sie

```C
_set_new_mode(1);
```

rechtzeitig im Programm auf, oder stellen Sie eine Verknüpfung mit NEWMODE.OBJ her.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, **wird _recalloc** in [_recalloc_dbg](recalloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** markiert `__declspec(noalias)` `__declspec(restrict)`ist und , was bedeutet, dass die Funktion garantiert keine globalen Variablen ändert und dass der zurückgegebene Zeiger nicht aliasiert wird. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> und \<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[kostenlos](free.md)<br/>
[Linkoptionen](../../c-runtime-library/link-options.md)<br/>
