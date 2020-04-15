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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341575"
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

*Größe*<br/>
Zuzuordnende Bytes.

## <a name="return-value"></a>Rückgabewert

**malloc** gibt einen leeren Zeiger auf den zugewiesenen Speicherplatz oder **NULL** zurück, wenn nicht genügend Arbeitsspeicher verfügbar ist. Um einen Zeiger auf einen anderen Typ als **void**zurückzugeben, verwenden Sie einen Typ, der für den Rückgabewert zurückgeworfen wird. Es ist sichergestellt, dass der Speicherplatz, auf den der Rückgabewert zeigt, passend für einen Speicher von einem beliebigen Objekttyp ist, dessen Ausrichtungsanforderungen kleiner oder gleich der grundlegenden Ausrichtung sind. (In Visual C++ ist die grundlegende Ausrichtung die Ausrichtung, die für ein **Double**oder 8 Bytes erforderlich ist. In Code, der auf 64-Bit-Plattformen abzielt, sind es 16 Bytes.) Verwenden Sie [_aligned_malloc,](aligned-malloc.md) um Speicher für Objekte zuzuweisen, die eine größere Ausrichtungsanforderung aufweisen, `__declspec(align( n ))` z. B. die SSE-Typen [__m128](../../cpp/m128.md) und **__m256**und Typen, die deklariert werden, indem sie die Datei **n** größer als 8 verwenden. Wenn *die Größe* 0 ist, weist **malloc** ein Element mit einer Länge von Null im Heap zu und gibt einen gültigen Zeiger auf dieses Element zurück. Überprüfen Sie immer die Rücksendung von **malloc**, auch wenn die angeforderte Speichermenge gering ist.

## <a name="remarks"></a>Bemerkungen

Die **malloc-Funktion** weist einen Speicherblock mit mindestens *großen* Bytes zu. Der Block kann aufgrund des Platzes, der für Ausrichtungs- und Wartungsinformationen erforderlich ist, größer als *die Größe* von Bytes sein.

**malloc** legt **errno** auf **ENOMEM** fest, wenn eine Speicherzuweisung fehlschlägt oder wenn die angeforderte Speichermenge **_HEAP_MAXREQ**übersteigt. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Der Startcode verwendet **malloc,** um Speicher für die Variablen **_environ**, *envp*und *argv* zuzuweisen. Die folgenden Funktionen und ihre breitstelligen Gegenstücke rufen auch **malloc**auf.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec functions](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[System](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[Getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[führt zu](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

Die C++-Funktion [_set_new_mode](set-new-mode.md) legt den neuen Handlermodus für **malloc** fest. Der neue Handlermodus gibt an, ob **malloc** bei einem Fehler die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **malloc** die neue Handlerroutine bei Nichtzuweisung von Arbeitsspeicher nicht auf. Sie können dieses Standardverhalten überschreiben, sodass **malloc** die neue Handlerroutine auf die gleiche Weise aufruft, wenn **malloc** keinen Speicher zuweist, wie der **neue** Operator dies tut, wenn er aus demselben Grund fehlschlägt. Um die Standardeinstellung `_set_new_mode(1)` zu überschreiben, rufen Sie das Programm frühzeitig auf oder verknüpfen Sie es mit NEWMODE. OBJ (siehe [Linkoptionen](../../c-runtime-library/link-options.md)).

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **malloc** [in _malloc_dbg](malloc-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [Details zum CRT-Debugheap](/visualstudio/debugger/crt-debug-heap-details).

**malloc** ist `__declspec(noalias)` `__declspec(restrict)`markiert und ; Dies bedeutet, dass die Funktion garantiert keine globalen Variablen ändert und dass der zurückgegebene Zeiger nicht mit einem Alias bezeichnet wird. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
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

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[kostenlos](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
