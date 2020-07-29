---
title: memchr, wmemchr
ms.date: 03/31/2019
api_name:
- wmemchr
- memchr
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memchr
- wmemchr
helpviewer_keywords:
- memchr function
- wmemchr function
ms.assetid: 5a348581-28f1-4256-8434-687245f7fc9f
ms.openlocfilehash: b4640004526eda4ff26e9601e15298bcb8ba3c79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232468"
---
# <a name="memchr-wmemchr"></a>memchr, wmemchr

Suchen nach Zeichen in einem Puffer.

## <a name="syntax"></a>Syntax

```C
void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C only
void *memchr(
   void *buffer,
   int c,
   size_t count
); // C++ only
const void *memchr(
   const void *buffer,
   int c,
   size_t count
); // C++ only
wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C only
wchar_t *wmemchr(
   wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
const wchar_t *wmemchr(
   const wchar_t * buffer,
   wchar_t c,
   size_t count
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Ein Zeiger auf einen Puffer.

*scher*<br/>
Zu suchendes Zeichen.

*count*<br/>
Anzahl der zu prüfenden Zeichen.

## <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, wird ein Zeiger auf die erste Position von *c* im *Puffer*zurückgegeben. Andernfalls wird NULL zurückgegeben.

## <a name="remarks"></a>Bemerkungen

`memchr`und `wmemchr` Suchen nach dem ersten Vorkommen von *c* in den ersten *zählungs* Zeichen des *Puffers*. Sie wird beendet, wenn Sie *c* findet oder wenn Sie die ersten *Anzahl* von Zeichen geprüft hat.

In C akzeptieren diese Funktionen einen **`const`** Zeiger auf das erste Argument. In C++ sind zwei Überladungen verfügbar. Die Überladung, die einen Zeiger auf annimmt, **`const`** gibt einen Zeiger auf zurück **`const`** . die Version, die einen Zeiger auf nicht-zurücknimmt, **`const`** gibt einen Zeiger auf nicht-zurück **`const`** . Die \_ Konstanten CRT \_ \_ \_ -konstantenüberladungen werden definiert, wenn sowohl die **`const`** -Version als auch die nicht-- **`const`** Version dieser Funktionen verfügbar sind. Wenn Sie das nicht-- **`const`** Verhalten für beide C++-über Ladungen in C++ benötigen, definieren Sie das Symbol \_ Konstanten \_ Rückgabe.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`memchr`|\<memory.h> oder \<string.h>|
|`wmemchr`|\<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_memchr.c

#include <memory.h>
#include <stdio.h>

int  ch = 'r';
char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;
   printf( "String to be searched:\n             %s\n", string );
   printf( "             %s\n             %s\n\n", fmt1, fmt2 );

   printf( "Search char: %c\n", ch );
   pdest = memchr( string, ch, sizeof( string ) );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "Result:      %c found at position %d\n", ch, result );
   else
      printf( "Result:      %c not found\n" );
}
```

### <a name="output"></a>Output

```Output
String to be searched:
             The quick brown dog jumps over the lazy fox
                      1         2         3         4         5
             12345678901234567890123456789012345678901234567890

Search char: r
Result:      r found at position 12
```

## <a name="see-also"></a>Siehe auch

[Puffer Bearbeitung](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
