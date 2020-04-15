---
title: strerror, _strerror, _wcserror, __wcserror
description: Beschreibt die Microsoft C-Runtime Library(CRT)-Funktionen strerror, _strerror, _wcserror und __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337330"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Ruft eine Systemfehlermeldungszeichenfolge ab (**strerror**, **_wcserror**) oder formatiert eine vom Benutzer bereitgestellte Fehlermeldungszeichenfolge (**_strerror**, **__wcserror**). Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Syntax

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Parameter

*errnum*\
Fehlernummer.

*strErrMsg*\
Vom Benutzer angegebene Meldung.

## <a name="return-value"></a>Rückgabewert

Alle diese Funktionen geben einen Zeiger auf eine Fehlermeldungszeichenfolge in einem threadlokalen Speicherpuffer zurück, der der Laufzeit gehört. Spätere Aufrufe desselben Threads können diese Zeichenfolge überschreiben.

## <a name="remarks"></a>Bemerkungen

Die **strerror-Funktion** ordnet *errnum* einer Fehlermeldungszeichenfolge zu und gibt einen Zeiger auf die Zeichenfolge zurück. Die **Funktionen strerror** und **_strerror** drucken die Nachricht nicht. Um zu drucken, rufen Sie eine Ausgabefunktion wie [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)auf:

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Wenn *strErrMsg* als **NULL**übergeben wird, **gibt _strerror** einen Zeiger auf eine Zeichenfolge zurück. Sie enthält die Systemfehlermeldung für den letzten Bibliotheksaufruf, bei dem ein Fehler aufgetreten ist. Die Fehlermeldungszeichenfolge wird durch das Zeilenumbruchzeichen ('\n') beendet. Wenn *strErrMsg* nicht **NULL**ist, enthält die Zeichenfolge in der Reihenfolge: Ihre *strErrMsg-Zeichenfolge,* einen Doppelpunkt, ein Leerzeichen, die Systemfehlermeldung und ein Zeilenumleinenzeichen. Ihre Zeichenfolgennachricht kann höchstens 94 Zeichen lang sein, entweder in schmalen (**_strerror)** oder breiten (**__wcserror**) Zeichen.

Die tatsächliche Fehlernummer für **_strerror** wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)gespeichert. Um genaue Ergebnisse zu erzielen, rufen **Sie _strerror** sofort auf, nachdem eine Bibliotheksroutine einen Fehler zurückgegeben hat. Andernfalls können spätere Aufrufe von Bibliotheksroutinen den **Errnowert** überschreiben.

**_wcserror** und **__wcserror** sind breitstellige Versionen von **strerror** bzw. **_strerror**.

**_strerror**, **_wcserror**und **__wcserror** sind Microsoft-spezifisch und nicht Teil der Standard-C-Bibliothek. Wir empfehlen Ihnen nicht, sie dort zu verwenden, wo Sie portablen Code benötigen. Verwenden Sie für Standard C-Kompatibilität stattdessen **strerror.**

Um Fehlerzeichenfolgen zu erhalten, empfehlen wir **strerror** oder **_wcserror** anstelle der veralteten Makros [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) und [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) und der veralteten internen Funktionen **__sys_errlist** und **__sys_nerr**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Generische Sertägliche Routinezuordnungen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Betrachten Sie das Beispiel für [perror](perror-wperror.md).

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)\
[klarer](clearerr.md)\
[Ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
