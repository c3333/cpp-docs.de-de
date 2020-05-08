---
title: clearerr_s
ms.date: 4/2/2020
api_name:
- clearerr_s
- _o_clearerr_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 3e300562a52029fe835ebd4fe34e9a7ef247a76a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917208"
---
# <a name="clearerr_s"></a>clearerr_s

Setzt den Fehlerindikator für einen Stream zurück. Dies ist eine sicherere Version von [clearerr](clearerr.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger auf **Datei** Struktur

## <a name="return-value"></a>Rückgabewert

NULL, wenn erfolgreich; **EINVAL** , wenn der *Stream* **null**ist.

## <a name="remarks"></a>Hinweise

Die **clearerr_s** -Funktion setzt den Fehler Indikator und den Dateiende-Indikator für den *Stream*zurück. Fehlerindikatoren werden nicht automatisch gelöscht. Sobald der Fehler Indikator für einen angegebenen Stream festgelegt ist, geben Vorgänge in diesem Stream weiterhin einen Fehlerwert zurück, bis **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**oder [Rewind](rewind.md) aufgerufen wird.

Wenn *stream* der Stream **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion " **errno** " auf " **EINVAL** " fest und gibt " **EINVAL**" zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>Eingabe

```Input
n
```

### <a name="output"></a>Output

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Siehe auch

[Fehlerbehandlung](../../c-runtime-library/error-handling-crt.md)<br/>
[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
