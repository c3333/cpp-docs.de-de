---
title: calloc
description: Die C-Laufzeitbibliotheksfunktion calloc weist Null-Initialisierten Speicher zu.
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333651"
---
# <a name="calloc"></a>calloc

Ordnet ein Array im Arbeitsspeicher mit Elementen an, die auf 0 initialisiert sind.

## <a name="syntax"></a>Syntax

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parameter

*number*<br/>
Anzahl der Elemente.

*Größe*<br/>
Länge jedes Elements in Bytes.

## <a name="return-value"></a>Rückgabewert

**calloc** gibt einen Zeiger auf den zugewiesenen Speicherplatz zurück. Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um einen Zeiger auf einen anderen Typ als **void**abzubekommen, verwenden Sie einen Typ, der für den Rückgabewert zurückgeworfen wird.

## <a name="remarks"></a>Bemerkungen

Die **calloc-Funktion** reserviert Speicherplatz für ein Array von *Zahlenelementen* mit jeweils mehreren Bytes in der *Längengröße.* Jedes Element wird auf 0 initialisiert.

**calloc** legt **errno** auf **ENOMEM** fest, wenn eine Speicherzuweisung fehlschlägt oder wenn die angeforderte Speichermenge **_HEAP_MAXREQ**übersteigt. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wenn in der Microsoft-Implementierung *die Anzahl* oder *Größe* Null ist, gibt **calloc** einen Zeiger auf einen zugewiesenen Block mit einer Größe ungleich Null zurück. Ein Versuch, den zurückgegebenen Zeiger zu lesen oder zu schreiben, führt zu einem undefinierten Verhalten.

**calloc** verwendet die [C++-_set_new_mode-Funktion,](set-new-mode.md) um den *neuen Handlermodus*festzulegen. Der neue Handlermodus gibt an, ob **calloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **calloc** die neue Handlerroutine bei Nichtzuweisung von Arbeitsspeicher nicht auf. Sie können dieses Standardverhalten überschreiben, sodass **calloc,** wenn er keinen Arbeitsspeicher zuweist, die neue Handlerroutine auf die gleiche Weise aufruft wie der **neue** Operator, wenn er aus dem gleichen Grund fehlschlägt. Um den Standardwert zu überschreiben, rufen Sie

```C
_set_new_mode(1);
```

oder eine Verknüpfung mit *NEWMODE. OBJ* (siehe [Linkoptionen](../../c-runtime-library/link-options.md)).

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **calloc** [in _calloc_dbg](calloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**calloc** ist `__declspec(noalias)` `__declspec(restrict)`markiert und , was bedeutet, dass die Funktion garantiert keine globalen Variablen ändert und dass der zurückgegebene Zeiger nicht aliasiert wird. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**calloc**|\<stdlib.h> und \<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[kostenlos](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
