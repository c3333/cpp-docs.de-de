---
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 64b9abe6313cc13e1e20f8f66ba486cdeb3e4892
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919333"
---
# <a name="perror-_wperror"></a>perror, _wperror

Druckt eine Fehlermeldung.

## <a name="syntax"></a>Syntax

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>Parameter

*message*<br/>
Zu druckende Zeichenfolgennachricht.

## <a name="remarks"></a>Hinweise

Die **perror** -Funktion gibt eine Fehlermeldung an **stderr**aus. **_wperror** ist eine breit Zeichen Version von **_perror**. Das *Nachrichten* Argument für **_wperror** ist eine Zeichenfolge mit breit Zeichen. **_wperror** und **_perror** Verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

Zuerst wird die *Nachricht* gedruckt, gefolgt von einem Doppelpunkt, dann nach der System Fehlermeldung für den letzten Bibliotheks Befehl, der den Fehler erzeugt hat, und schließlich nach einem Zeilen vorzeilenzeichen. Wenn *Message* ein NULL-Zeiger oder ein Zeiger auf eine NULL-Zeichenfolge ist, druckt **perror** nur die System Fehlermeldung.

Die Fehlernummer wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (in ERRNO.H definiert) gespeichert. Über die Variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) wird auf die Systemfehlermeldungen zugegriffen, die als Array von Meldungen nach Fehlernummern geordnet sind. **perror** druckt die entsprechende Fehlermeldung mit dem **errno** -Wert als Index für **_sys_errlist**. Der Wert der Variablen [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) die als maximale Anzahl von Elementen im **_sys_errlist** Array definiert ist.

Um genaue Ergebnisse zu erhalten, wird durch Aufrufen von **perror** sofort nach der Rückgabe einer Bibliotheks Routine mit einem Fehler aufgerufen. Andernfalls können nachfolgende Aufrufe den **errno** -Wert überschreiben.

Im Windows-Betriebssystem gibt es einige **errno** -Werte, die in errno aufgeführt sind. H wird nicht verwendet. Diese Werte sind für die Verwendung des UNIX-Betriebssystems reserviert. Eine Auflistung von **errno** -Werten, die vom Windows-Betriebssystem verwendet werden, finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) . **perror** gibt eine leere Zeichenfolge für einen **errno** -Wert aus, der nicht von diesen Plattformen verwendet wird.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**perror**|\<stdio.h > oder \<stdlib.h >|
|**_wperror**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
