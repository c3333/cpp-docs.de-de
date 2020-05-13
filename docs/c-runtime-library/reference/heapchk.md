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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2ddbdaec5861d48cc23a7cbcd28332e8c06ebbfe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916214"
---
# <a name="_heapchk"></a>_heapchk

Führt Konsistenzüberprüfungen auf dem Heap aus.

## <a name="syntax"></a>Syntax

```C
int _heapchk( void );
```

## <a name="return-value"></a>Rückgabewert

**_heapchk** gibt eine der folgenden ganzzahligen Manifest-Konstanten zurück, die in malloc. h definiert sind.

|Rückgabewert|Bedingung|
|-|-|
| **_HEAPBADBEGIN** | Die ursprüngliche Headerinformation ist schlecht oder wurde nicht gefunden. |
| **_HEAPBADNODE** | Ein ungültiger Knoten wurde gefunden, oder Heap ist beschädigt. |
| **_HEAPBADPTR** | Der Zeiger auf einen Heap ist ungültig. |
| **_HEAPEMPTY** | Der Heap wurde noch nicht initialisiert. |
| **_HEAPOK** | Der Heap scheint konsistent zu sein. |

Wenn ein Fehler auftritt, legt **_heapchk** außerdem **errno** auf **enosys**fest.

## <a name="remarks"></a>Hinweise

Die **_heapchk** -Funktion unterstützt das Debuggen von Heap bezogenen Problemen durch die Überprüfung auf minimale Konsistenz des Heaps. Wenn das Betriebssystem **_heapchk**nicht unterstützt (z. b. Windows 98), gibt die Funktion **_HEAPOK** zurück und legt **errno** auf **enosys**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
