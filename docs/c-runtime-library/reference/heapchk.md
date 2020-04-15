---
title: _heapchk
ms.date: 4/2/2020
api_name:
- _heapchk
- _o__heapchk
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
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 21c7f9e22728109676d3fc611405ccd43ac773f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344056"
---
# <a name="_heapchk"></a>_heapchk

Führt Konsistenzüberprüfungen auf dem Heap aus.

## <a name="syntax"></a>Syntax

```C
int _heapchk( void );
```

## <a name="return-value"></a>Rückgabewert

**_heapchk** gibt eine der folgenden ganzzahligen Manifestkonstanten zurück, die in Malloc.h definiert sind.

|Rückgabewert|Bedingung|
|-|-|
| **_HEAPBADBEGIN** | Die ursprüngliche Headerinformation ist schlecht oder wurde nicht gefunden. |
| **_HEAPBADNODE** | Ein ungültiger Knoten wurde gefunden, oder Heap ist beschädigt. |
| **_HEAPBADPTR** | Der Zeiger auf einen Heap ist ungültig. |
| **_HEAPEMPTY** | Der Heap wurde noch nicht initialisiert. |
| **_HEAPOK** | Der Heap scheint konsistent zu sein. |

Wenn ein Fehler auftritt, setzt _heapchk **errno** auf **_heapchk** **ENOSYS**.

## <a name="remarks"></a>Bemerkungen

Die **_heapchk-Funktion** hilft beim Debuggen von Heapproblemen, indem sie auf minimale Konsistenz des Heaps überprüft. Wenn das Betriebssystem **_heapchk**(z. B. Windows 98) nicht unterstützt, gibt die Funktion **_HEAPOK** zurück und setzt **errno** auf **ENOSYS**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
