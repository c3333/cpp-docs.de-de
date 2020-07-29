---
title: calloc
description: Die C-Lauf Zeit Bibliotheksfunktion "cbelegc" ordnet NULL initialisierten Arbeitsspeicher zu.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 067ce6f347f4b24ad8c85990e70fe4d79305535c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213631"
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

*Zahl*<br/>
Anzahl der Elemente.

*size*<br/>
Länge jedes Elements in Bytes.

## <a name="return-value"></a>Rückgabewert

**czuzuordnungs** gibt einen Zeiger auf den zugeordneten Speicherplatz zurück. Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um einen Zeiger auf einen anderen Typ als zu erhalten **`void`** , verwenden Sie eine Typumwandlung für den Rückgabewert.

## <a name="remarks"></a>Bemerkungen

Die **czuzuordnungsfunktion** ordnet Speicherplatz für ein Array von *Zahlen* Elementen zu, die jeweils *eine Länge von* Bytes haben. Jedes Element wird auf 0 initialisiert.

**calloc** legt **errno** auf " **endomem** " fest, wenn eine Speicher Belegung fehlschlägt oder wenn die Menge an Angeforderter Arbeitsspeicher **_HEAP_MAXREQ**überschreitet. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Wenn die *Anzahl* oder *Größe* in der Microsoft-Implementierung NULL ist, gibt **czuzuordc** einen Zeiger auf einen zugeordneten Block ungleich 0 (null) zurück. Der Versuch, den zurückgegebenen Zeiger zu lesen oder zu schreiben, führt zu nicht definiertem Verhalten.

**czuzuordnungs** verwendet die C++ [_set_new_mode](set-new-mode.md) -Funktion, um den *neuen handlermodus*festzulegen. Der neue handlermodus gibt an, ob **czuzubei** einem Fehler die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **calloc** die neue Handlerroutine bei einem Fehler bei der Speicherzuweisung nicht auf. Sie können dieses Standardverhalten außer Kraft setzen, sodass, wenn **calloc** keinen Arbeitsspeicher zuordnen kann, die neue Handlerroutine genauso aufruft wie der- **`new`** Operator, wenn dieser aus demselben Grund fehlschlägt. Um den Standardwert zu überschreiben, rufen Sie

```C
_set_new_mode(1);
```

frühzeitig in Ihrem Programm oder mit *NEWMODE verknüpfen. Obj* (siehe [Link Optionen](../../c-runtime-library/link-options.md)).

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird " **czuzuordc** " in " [_calloc_dbg](calloc-dbg.md)" aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

**czuweisung** ist `__declspec(noalias)` als und gekennzeichnet `__declspec(restrict)` , was bedeutet, dass die Funktion keine globalen Variablen ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
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

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[Kosten](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
