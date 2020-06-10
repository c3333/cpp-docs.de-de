---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 06/09/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 91be8803a0695670e7afe673b25b54fccde40a9c
ms.sourcegitcommit: 8167c67d76de58a7c2df3b4dcbf3d53e3b151b77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84664325"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Eine System Fehlermeldung (**strerror_s**, **_wcserror_s**) oder eine vom Benutzer bereitgestellte Fehlermeldung (**_strerror_s**, **__wcserror_s**) erhalten. Dies sind Versionen von [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t strerror_s(
   char *buffer,
   size_t sizeInBytes,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t sizeInBytes,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t sizeInWords,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Puffer für die Fehlerzeichenfolge.

*sizeInBytes*<br/>
Die Anzahl von Bytes im Puffer.

*sizin words*<br/>
Die Anzahl der Wörter im Puffer.

*errnum*<br/>
Fehlernummer.

*"Strauch Meldung"*<br/>
Vom Benutzer angegebene Meldung.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

### <a name="error-condtions"></a>Fehlerbedingungen

|*ert*|*sizin Bytes/sizeIn words*|*"Strauch Meldung"*|Inhalt des *Puffers*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|any|any|–|
|any|0|any|nicht geändert|

## <a name="remarks"></a>Bemerkungen

Die **strerror_s** -Funktion ordnet *errnum* einer Fehlermeldungs Zeichenfolge zu und gibt die Zeichenfolge im *Puffer*zurück. **_strerror_s** nimmt die Fehlernummer nicht an. Er verwendet den aktuellen Wert von **errno** , um die entsprechende Meldung zu bestimmen. Weder **strerror_s** noch **_strerror_s** gibt die Nachricht tatsächlich aus: dafür müssen Sie eine Ausgabefunktion wie z. b. [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)aufrufen:

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Wenn " *strauerrmsg* " den Wert **null**hat, gibt **_strerror_s** eine Zeichenfolge im *Puffer* zurück, die die System Fehlermeldung für den letzten Bibliotheks Rückruf enthält, der einen Fehler verursacht hat. Die Fehlermeldungszeichenfolge wird durch das Zeilenumbruchzeichen ('\n') beendet. Wenn " *stringermsg* " nicht gleich **null**ist, gibt **_strerror_s** eine Zeichenfolge im *Puffer* zurück, die (in der richtigen Reihenfolge) die Zeichen folgen Meldung, einen Doppelpunkt, ein Leerzeichen, die System Fehlermeldung für den letzten Bibliotheks Aufrufern, der einen Fehler erzeugt, und ein Zeilen Vorzeichen Die Zeichenfolgenmeldung darf höchstens 94 Zeichen lang sein.

Diese Funktionen schneiden die Fehlermeldung ab, wenn Ihre Länge die Größe des Puffers-1 überschreitet. Die resultierende Zeichenfolge im *Puffer* wird immer mit Null beendet.

Die tatsächliche Fehlernummer für **_strerror_s** wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)gespeichert. Über die Variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) wird auf die Systemfehlermeldungen zugegriffen, die als Array von Meldungen nach Fehlernummern geordnet sind. **_strerror_s** greift auf die entsprechende Fehlermeldung zu, indem der **errno** -Wert als Index für die Variable **_sys_errlist**verwendet wird. Der Wert der Variablen [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) die als maximale Anzahl von Elementen im **_sys_errlist** Array definiert ist. Um genaue Ergebnisse zu erzielen, rufen Sie **_strerror_s** sofort auf, nachdem eine Bibliotheks Routine mit einem Fehler zurückgegeben wurde. Andernfalls können nachfolgende Aufrufe von **strerror_s** oder **_strerror_s** den **errno** -Wert überschreiben.

**_wcserror_s** und **__wcserror_s** sind breit Zeichen Versionen von **strerror_s** bzw. **_strerror_s**.

Diese Funktionen überprüfen ihre Parameter. Wenn der Puffer **null** ist oder der Size-Parameter den Wert 0 hat, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **EINVAL** zurück und legen **errno** auf **EINVAL**fest.

**_strerror_s**, **_wcserror_s**und **__wcserror_s** sind nicht Teil der ANSI-Definition, sondern sind stattdessen Microsoft-Erweiterungen. Verwenden Sie diese nicht, wenn Portabilität gewünscht ist. Verwenden Sie für die ANSI-Kompatibilität stattdessen **strerror_s** .

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**strerror_s** **_strerror_s**|\<string.h>|
|**_wcserror_s** **__wcserror_s**|\<string.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Betrachten Sie das Beispiel für [perror](perror-wperror.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
