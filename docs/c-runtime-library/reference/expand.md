---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347559"
---
# <a name="_expand"></a>_expand

Ändert die Größe eines Speicherblocks.

## <a name="syntax"></a>Syntax

```C
void *_expand(
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

**_expand** gibt einen leeren Zeiger auf den neu verteilten Speicherblock zurück. **_expand**kann im Gegensatz zu **realloc**einen Block nicht verschieben, um seine Größe zu ändern. Wenn also genügend Arbeitsspeicher verfügbar ist, um den Block zu erweitern, ohne ihn zu verschieben, ist der *memblock-Parameter* in **_expand** derselbe wie der Rückgabewert.

**_expand** gibt **NULL** zurück, wenn während des Betriebs ein Fehler erkannt wird. Wenn **z.** B. _expand zum Verkleinern eines Speicherblocks verwendet wird, kann es sein, dass eine Beschädigung im kleinen Blockheap oder in einem ungültigen Blockzeiger erkannt wird, und **NULL**zurückgibt.

Wenn nicht genügend Arbeitsspeicher verfügbar ist, um den Block auf die angegebene Größe zu erweitern, ohne ihn zu verschieben, gibt die Funktion **NULL**zurück. **_expand** gibt nie einen Block zurück, der auf eine Größe kleiner als angefordert erweitert wurde. Wenn ein Fehler auftritt, gibt **errno** die Art des Fehlers an. Weitere Informationen zu **errno**finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um die neue Größe des Elements zu überprüfen, verwenden Sie **_msize**. Um einen Zeiger auf einen anderen Typ als **void**abzubekommen, verwenden Sie einen Typ, der für den Rückgabewert zurückgeworfen wird.

## <a name="remarks"></a>Bemerkungen

Die **_expand-Funktion** ändert die Größe eines zuvor zugewiesenen Speicherblocks, indem versucht wird, den Block zu erweitern oder zu verkleinern, ohne seine Position im Heap zu verschieben. Der *Memblock-Parameter* zeigt auf den Anfang des Blocks. Der *Größenparameter* gibt die neue Größe des Blocks in Bytes an. Der Inhalt des Blocks bleibt bis zum Minimum von neuer und alter Größe unverändert. *memblock* sollte kein Block sein, der freigegeben wurde.

> [!NOTE]
> Auf 64-Bit-Plattformen **_expand** den Block möglicherweise nicht zusammenziehen, wenn die neue Größe kleiner als die aktuelle Größe ist. Insbesondere wenn der Block weniger als 16K groß war und daher im Low Fragmentation Heap zugeordnet wurde, lässt **_expand** den Block unverändert und gibt *memblock*zurück.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, **wird _expand** in [_expand_dbg](expand-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

Diese Funktion überprüft ihre Parameter. Wenn *memblock* ein Nullzeiger ist, ruft diese Funktion einen ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt, und die Funktion gibt **NULL**zurück. Wenn *die Größe* größer als **_HEAP_MAXREQ**ist, wird **errno** auf **ENOMEM** gesetzt, und die Funktion gibt **NULL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[kostenlos](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
