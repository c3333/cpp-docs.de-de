---
title: strerror, _strerror, _wcserror, __wcserror
description: Beschreibt die Funktionen von Microsoft C-Lauf Zeit Bibliothek (CRT), _strerror, _wcserror und __wcserror.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 30885974b9c9fbf0fdca0e52808fb8bd1dfbaffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920032"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Ruft eine Fehlermeldungs Zeichenfolge für eine System Fehlermeldung (" **_wcserror**") ab oder**formatiert**eine vom Benutzer bereitgestellte Fehlermeldungs Zeichenfolge (**_strerror** **__wcserror** Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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

*"Strauch Meldung"*\
Vom Benutzer angegebene Meldung.

## <a name="return-value"></a>Rückgabewert

Alle diese Funktionen geben einen Zeiger auf eine Fehlermeldungs Zeichenfolge in einem Thread lokalen Speicherpuffer zurück, der im Besitz der Laufzeit ist. Spätere Aufrufe für denselben Thread können diese Zeichenfolge überschreiben.

## <a name="remarks"></a>Hinweise

Die " **strauerror** "-Funktion ordnet *errnum* einer Fehlermeldungs Zeichenfolge zu und gibt einen Zeiger auf die Zeichenfolge zurück. Die Funktionen " **strauerror** " und " **_strerror** " Drucken die Nachricht nicht. Zum Drucken können Sie eine Ausgabefunktion wie z. [b. fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)aufrufen:

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Wenn *"* " "" "" als **null**-Wert, **_strerror** einen Zeiger auf eine Zeichenfolge zurückgegeben. Sie enthält die System Fehlermeldung für den letzten Bibliotheks Rückruf, der einen Fehler verursacht hat. Die Fehlermeldungszeichenfolge wird durch das Zeilenumbruchzeichen ('\n') beendet. Wenn " *darerrmsg* " nicht **null**ist, enthält die Zeichenfolge in der angegebenen Reihenfolge: die Zeichenfolge " *darerrmsg* ", ein Doppelpunkt, ein Leerzeichen, die System Fehlermeldung und ein Zeilen vorzeitiges Zeichen. Die Zeichen folgen Nachricht kann höchstens 94 Zeichen lang sein, entweder in schmalen (**_strerror**) oder breiten Zeichen (**__wcserror**).

Die tatsächliche Fehlernummer für **_strerror** wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)gespeichert. Um genaue Ergebnisse zu erzielen, rufen Sie **_strerror** sofort auf, nachdem eine Bibliotheks Routine einen Fehler zurückgegeben hat. Andernfalls können spätere Aufrufe von Bibliotheks Routinen den **errno** -Wert überschreiben.

**_wcserror** und **__wcserror** sind breit Zeichen Versionen von " **strauerror** " bzw. " **_strerror**".

**_strerror**, **_wcserror**und **__wcserror** sind Microsoft-spezifisch, nicht Teil der Standard-C-Bibliothek. Wir empfehlen Ihnen nicht, Sie zu verwenden, wenn Sie portablen Code verwenden möchten. Verwenden Sie für die Standard-C-Kompatibilität stattdessen " **strauerror** ".

Um Fehler Zeichenfolgen zu erhalten, **_wcserror** **empfehlen wir** anstelle der veralteten Makros [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) und [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) sowie die veralteten internen Funktionen **__sys_errlist** und **__sys_nerr**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnungen von generischen Text Routinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror** **__wcserror**|\<string.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Betrachten Sie das Beispiel für [perror](perror-wperror.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)\
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
