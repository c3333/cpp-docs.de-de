---
title: realloc
ms.date: 4/2/2020
api_name:
- realloc
- _o_realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332931"
---
# <a name="realloc"></a>realloc

Neubelegung von Arbeitsspeicherblöcken.

## <a name="syntax"></a>Syntax

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parameter

*memblock*<br/>
Zeiger zum vorherigen belegten Speicherblock.

*Größe*<br/>
Neue Größe in Bytes.

## <a name="return-value"></a>Rückgabewert

**realloc** gibt einen **leeren** Zeiger auf den neu verteilten (und möglicherweise verschobenen) Speicherblock zurück.

Wenn nicht genügend Arbeitsspeicher verfügbar ist, um den Block auf die angegebene Größe zu erweitern, bleibt der ursprüngliche Block unverändert, und **NULL** wird zurückgegeben.

Wenn *die Größe* Null ist, wird der Block, auf den *memblock* zeigt, freigegeben. Der Rückgabewert ist **NULL**, und *memblock* bleibt links und zeigt auf einen freigegebenen Block.

Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um einen Zeiger auf einen anderen Typ als **void**abzubekommen, verwenden Sie einen Typ, der für den Rückgabewert zurückgeworfen wird.

## <a name="remarks"></a>Bemerkungen

Die **Realloc-Funktion** ändert die Größe eines zugewiesenen Speicherblocks. Das *memblock-Argument* zeigt auf den Anfang des Speicherblocks. Wenn *memblock* **NULL**ist, verhält sich **realloc** genauso wie **malloc** und weist einen neuen Block von *Größenbytes* zu. Wenn *memblock* nicht **NULL**ist, sollte es sich um einen Zeiger handelt, der von einem vorherigen Aufruf von **calloc**, **malloc**oder **realloc**zurückgegeben wird.

Das *Size-Argument* gibt die neue Größe des Blocks in Bytes an. Der Inhalt des Blocks bleibt bis zum Minimum von neuer und alter Größe unverändert, obwohl sich der neue Block an einem anderen Speicherort befinden kann. Da sich der neue Block an einer neuen Speicherposition befinden kann, ist der von **realloc** zurückgegebene Zeiger nicht garantiert der Zeiger, der durch das *memblock-Argument* übergeben wird. **realloc** wird bei Pufferwachstum nicht auf Null des neu zugewiesenen Speichers gesetzt.

**realloc** legt **errno** auf **ENOMEM** fest, wenn die Speicherzuweisung fehlschlägt oder wenn die angeforderte Speichermenge **_HEAP_MAXREQ**übersteigt. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** ruft **malloc** auf, um die C++-_set_new_mode-Funktion zum Festlegen des neuen Handlermodus zu verwenden. [_set_new_mode](set-new-mode.md) Der neue Handlermodus gibt an, ob **malloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **malloc** die neue Handlerroutine bei Nichtzuweisung von Arbeitsspeicher nicht auf. Sie können dieses Standardverhalten überschreiben, sodass **malloc** die neue Handlerroutine auf die gleiche Weise aufruft, wenn **realloc** keinen Speicher zuweist, wie der **neue** Operator dies tut, wenn er aus demselben Grund fehlschlägt. Um den Standardwert zu überschreiben, rufen Sie

```C
_set_new_mode(1);
```

rechtzeitig im Programm auf, oder stellen Sie eine Verknüpfung mit NEWMODE.OBJ (siehe [Linkoptionen](../../c-runtime-library/link-options.md)) her.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **realloc** in [_realloc_dbg](realloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**realloc** ist `__declspec(noalias)` `__declspec(restrict)`markiert und , was bedeutet, dass die Funktion garantiert keine globalen Variablen ändert und dass der zurückgegebene Zeiger nicht aliasiert wird. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**realloc**|\<stdlib.h> und \<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[kostenlos](free.md)<br/>
[malloc](malloc.md)<br/>
