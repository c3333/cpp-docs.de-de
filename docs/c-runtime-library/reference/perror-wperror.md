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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338535"
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

*Nachricht*<br/>
Zu druckende Zeichenfolgennachricht.

## <a name="remarks"></a>Bemerkungen

Die **perror-Funktion** gibt eine Fehlermeldung an **stderr**aus. **_wperror** ist eine breitgefächerte Version von **_perror**; Das *Nachrichtenargument* für **_wperror** ist eine Zeichenfolge mit großen Zeichen. **_wperror** und **_perror** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**Perror**|**Perror**|**_wperror**|

*Die Nachricht* wird zuerst gedruckt, gefolgt von einem Doppelpunkt, dann von der Systemfehlermeldung für den letzten Bibliotheksaufruf, der den Fehler verursacht hat, und schließlich durch ein Zeilenumleinenzeichen. Wenn *die Nachricht* ein Nullzeiger oder ein Zeiger auf eine Nullzeichenfolge ist, druckt **perror** nur die Systemfehlermeldung.

Die Fehlernummer wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (in ERRNO.H definiert) gespeichert. Über die Variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) wird auf die Systemfehlermeldungen zugegriffen, die als Array von Meldungen nach Fehlernummern geordnet sind. **perror** druckt die entsprechende Fehlermeldung mit dem **errno-Wert** als Index für **_sys_errlist**. Der Wert der Variablen [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ist definiert als die maximale Anzahl von Elementen im **array _sys_errlist.**

Um genaue Ergebnisse zu erhalten, rufen Sie **perror** sofort auf, nachdem eine Bibliotheksroutine mit einem Fehler zurückgegeben wurde. Andernfalls können nachfolgende Aufrufe den **Errno-Wert** überschreiben.

Im Windows-Betriebssystem einige **errno-Werte** in ERRNO aufgeführt. H sind unbenutzt. Diese Werte sind für die Verwendung des UNIX-Betriebssystems reserviert. Eine Liste der vom Windows-Betriebssystem verwendeten **Errnowerte** finden Sie [unter _doserrno, errno, _sys_errlist und _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) **perror** druckt eine leere Zeichenfolge für einen **Errno-Wert,** der von diesen Plattformen nicht verwendet wird.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Perror**|\<stdio.h > oder \<stdlib.h >|
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

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
