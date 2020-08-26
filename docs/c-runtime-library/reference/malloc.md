---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: a093dbdbc4849b1c2f3d86e85a5e2b25a7b988e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836659"
---
# <a name="malloc"></a>malloc

Weist Speicherblöcke zu.

## <a name="syntax"></a>Syntax

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Zuzuordnende Bytes.

## <a name="return-value"></a>Rückgabewert

**malloc** gibt einen void-Zeiger auf den zugeordneten Speicherplatz oder **null** zurück, wenn nicht genügend Arbeitsspeicher verfügbar ist. Um einen Zeiger auf einen anderen Typ als zurückzugeben **`void`** , verwenden Sie eine Typumwandlung für den Rückgabewert. Es ist sichergestellt, dass der Speicherplatz, auf den der Rückgabewert zeigt, passend für einen Speicher von einem beliebigen Objekttyp ist, dessen Ausrichtungsanforderungen kleiner oder gleich der grundlegenden Ausrichtung sind. (In Visual C++ ist die grundlegende Ausrichtung die Ausrichtung, die für **`double`** oder 8 Bytes erforderlich ist. In Code, der auf 64-Bit-Plattformen ausgerichtet ist, sind es 16 Bytes.) Verwenden Sie [_aligned_malloc](aligned-malloc.md) , um Speicher für Objekte zuzuweisen, die eine größere Ausrichtungs Anforderung haben – z. b. die SSE-Typen [__m128](../../cpp/m128.md) und **`__m256`** und Typen, die mithilfe von deklariert werden, `__declspec(align( n ))` wobei **n** größer als 8 ist. Wenn die *Größe* 0 ist, ordnet **malloc** ein Element der Länge 0 (null) im Heap zu und gibt einen gültigen Zeiger auf dieses Element zurück. Überprüfen Sie immer die Rückgabe von **malloc**, auch wenn die Menge an Angeforderter Arbeitsspeicher gering ist.

## <a name="remarks"></a>Bemerkungen

Die **malloc** -Funktion weist einen Speicherblock mit mindestens *Größe* von Bytes zu. Der Block kann aufgrund des Platzes, der für die Ausrichtung und die Wartungsinformationen benötigt wird, größer als die *Größe* von Bytes sein.

**malloc** legt **errno** auf " **tomem** " fest, wenn eine Speicher Belegung fehlschlägt oder wenn die Menge an Angeforderter Arbeitsspeicher **_HEAP_MAXREQ**überschreitet. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Der Startcode verwendet **malloc** , um Speicher für die Variablen " **_environ**", " *SVP*" und " *argv* " zuzuweisen. Die folgenden Funktionen und ihre breit Zeichen Entsprechungen nennen auch **malloc**.

:::row:::
   :::column span="":::
      [calloc](calloc.md)\
      [_exec Funktionen](../../c-runtime-library/exec-wexec-functions.md)\
      [fgetc](fgetc-fgetwc.md)\
      [_fgetchar](fgetc-fgetwc.md)\
      [fgets](fgets-fgetws.md)\
      [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)\
      [fputc](fputc-fputwc.md)\
      [_fputchar](fputc-fputwc.md)\
      [fputs](fputs-fputws.md)\
      [fread](fread.md)
   :::column-end:::
   :::column span="":::
      [fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)\
      [fseek](fseek-fseeki64.md)\
      [fsetpos](fsetpos.md)\
      [_fullpath](fullpath-wfullpath.md)\
      [fwrite](fwrite.md)\
      [getc](getc-getwc.md)\
      [GetChar](getc-getwc.md)\
      [_getcwd](getcwd-wgetcwd.md)\
      [_getdcwd](getcwd-wgetcwd.md)\
      [kommt](../../c-runtime-library/gets-getws.md)
   :::column-end:::
   :::column span="":::
      [_getw](getw.md)\
      [_popen](popen-wpopen.md)\
      [printf](printf-printf-l-wprintf-wprintf-l.md)\
      [putc](putc-putwc.md)\
      [putchar](putc-putwc.md)\
      [_putenv](putenv-wputenv.md)\
      [legt](puts-putws.md)\
      [_putw](putw.md)\
      [scanf](scanf-scanf-l-wscanf-wscanf-l.md)
   :::column-end:::
   :::column span="":::
      [_searchenv](searchenv-wsearchenv.md)\
      [setvbuf](setvbuf.md)\
      [_spawn Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)\
      [_strdup](strdup-wcsdup-mbsdup.md)\
      [Anlage](system-wsystem.md)\
      [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)\
      [ungetc](ungetc-ungetwc.md)\
      [vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
      [vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)
   :::column-end:::
:::row-end:::

Die C++-Funktion [_set_new_mode](set-new-mode.md) legt den neuen Handlermodus für **malloc** fest. Der neue handlermodus gibt an, ob **malloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie Sie von [_set_new_handler](set-new-handler.md)festgelegt wird. Standardmäßig ruft **malloc** die neue Handlerroutine nicht bei einem Fehler auf, um Arbeitsspeicher zuzuweisen. Sie können dieses Standardverhalten überschreiben, sodass **malloc** die neue Handlerroutine auf dieselbe Weise aufruft, wenn **malloc** keinen Arbeitsspeicher zuordnen kann, **`new`** Wenn es aus demselben Grund fehlschlägt. Um den Standardwert zu überschreiben, sollten `_set_new_mode(1)` Sie früh im Programm aufzurufen oder mit NEWMODE verknüpfen. Obj (siehe [Link Optionen](../../c-runtime-library/link-options.md)).

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **malloc** zu [_malloc_dbg](malloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [Details zum CRT-Debugheap](/visualstudio/debugger/crt-debug-heap-details).

**malloc** ist `__declspec(noalias)` als und gekennzeichnet `__declspec(restrict)` . Dies bedeutet, dass die Funktion globale Variablen garantiert nicht ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**malloc**|\<stdlib.h> und \<malloc.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_malloc.c
// This program allocates memory with
// malloc, then frees the memory with free.

#include <stdlib.h>   // For _MAX_PATH definition
#include <stdio.h>
#include <malloc.h>

int main( void )
{
   char *string;

   // Allocate space for a path name
   string = malloc( _MAX_PATH );

   // In a C++ file, explicitly cast malloc's return.  For example,
   // string = (char *)malloc( _MAX_PATH );

   if( string == NULL )
      printf( "Insufficient memory available\n" );
   else
   {
      printf( "Memory space allocated for path name\n" );
      free( string );
      printf( "Memory freed\n" );
   }
}
```

```Output
Memory space allocated for path name
Memory freed
```

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[frei](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
