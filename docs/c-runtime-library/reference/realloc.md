---
title: realloc
description: API-Referenz für rezuweisung (); , wodurch Speicherblöcke neu zugewiesen werden.
ms.date: 9/11/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c68909b2f5d73959465d63af522ceeb00c8ce23e
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075815"
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

*`memblock`*\
Zeiger zum vorherigen belegten Speicherblock.

*`size`*\
Neue Größe in Bytes.

## <a name="return-value"></a>Rückgabewert

**`realloc`** Gibt einen **`void`** Zeiger auf den neu belegten (und möglicherweise verschobenden) Speicherblock zurück.

Wenn nicht genügend Arbeitsspeicher verfügbar ist, um den Block auf die angegebene Größe auszudehnen, bleibt der ursprüngliche Block unverändert, und **`NULL`** wird zurückgegeben.

Wenn *`size`* 0 (null) ist, wird der Block, auf den von verwiesen wird, *`memblock`* freigegeben. der Rückgabewert ist **`NULL`** , und *`memblock`* zeigt auf einen freigegebenen Block.

Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekt Typs geeignet ist. Um einen Zeiger auf einen anderen Typ als zu erhalten **`void`** , verwenden Sie eine Typumwandlung für den Rückgabewert.

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> **`realloc`** wurde nicht aktualisiert, um das C17-Verhalten zu implementieren, da das neue Verhalten nicht mit dem Windows-Betriebssystem kompatibel ist.

Die- **`realloc`** Funktion ändert die Größe eines zugeordneten Speicherblocks. Das- *`memblock`* Argument zeigt auf den Anfang des Speicherblocks. Wenn *`memblock`* **`NULL`** den Wert hat, **`realloc`** verhält sich wie **`malloc`** und ordnet einen neuen Block von *`size`* Bytes zu. Wenn *`memblock`* nicht ist **`NULL`** , sollte es sich um einen Zeiger handeln, der von einem vorherigen-Befehl von, oder zurückgegeben wurde **`calloc`** **`malloc`** **`realloc`** .

Das- *`size`* Argument gibt die neue Größe des Blocks in Bytes an. Der Inhalt des Blocks bleibt bis zum Minimum von neuer und alter Größe unverändert, obwohl sich der neue Block an einem anderen Speicherort befinden kann. Da sich der neue-Block an einem neuen Speicherort befinden kann, ist der Zeiger, der von zurückgegeben wird, **`realloc`** nicht garantiert der Zeiger, der durch das Argument geleitet wird *`memblock`* . **`realloc`** weist im Fall eines Puffer Wachstums keinen neu belegten Speicherplatz auf.

**`realloc`** legt **`errno`** auf fest, **`ENOMEM`** Wenn die Speicher Belegung fehlschlägt oder wenn die Menge an Angeforderter Arbeitsspeicher überschreitet **`_HEAP_MAXREQ`** . Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**`realloc`** Ruft auf, um mit **`malloc`** der C++ [_set_new_mode](set-new-mode.md) -Funktion den neuen handlermodus festzulegen. Der neue handlermodus gibt an, ob bei einem Fehler **`malloc`** die neue Handlerroutine aufgerufen werden soll, die von [_set_new_handler](set-new-handler.md)festgelegt wird. Standardmäßig **`malloc`** Ruft die neue Handlerroutine nicht bei einem Fehler auf, um Arbeitsspeicher zuzuweisen. Sie können dieses Standardverhalten außer Kraft setzen, sodass **`realloc`** **`malloc`** die neue Handlerroutine bei einem Fehler beim Zuordnen von Arbeitsspeicher auf dieselbe Weise aufgerufen wird, die der **`new`** Operator bei einem Fehler aus demselben Grund bewirkt. Um den Standardwert zu überschreiben, rufen Sie

```C
_set_new_mode(1);
```

rechtzeitig im Programm auf, oder stellen Sie eine Verknüpfung mit NEWMODE.OBJ (siehe [Linkoptionen](../../c-runtime-library/link-options.md)) her.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **`realloc`** in [_realloc_dbg](realloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**`realloc`** ist `__declspec(noalias)` als und gekennzeichnet `__declspec(restrict)` , was bedeutet, dass die Funktion globale Variablen garantiert nicht ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**`realloc`**|\<stdlib.h> und \<malloc.h>|

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

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)\
[calloc](calloc.md)\
[Kosten](free.md)\
[malloc](malloc.md)
