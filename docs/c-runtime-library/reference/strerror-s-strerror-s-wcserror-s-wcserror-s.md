---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337370"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Abrufen einer Systemfehlermeldung (**strerror_s**, **_wcserror_s**) oder Drucken einer vom Benutzer bereitgestellten Fehlermeldung (**_strerror_s**, **__wcserror_s**). Dies sind Versionen von [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
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

*Puffer*<br/>
Puffer für die Fehlerzeichenfolge.

*Sizeinbytes*<br/>
Puffergröße.

*errnum*<br/>
Fehlernummer.

*strErrMsg*<br/>
Vom Benutzer angegebene Meldung.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

### <a name="error-condtions"></a>Fehlerbedingungen

|*Puffer*|*Sizeinbytes*|*strErrMsg*|Inhalt des *Puffers*|
|--------------|------------------------|-----------------|--------------------------|
|**Null**|any|any|–|
|any|0|any|nicht geändert|

## <a name="remarks"></a>Bemerkungen

Die **strerror_s-Funktion** ordnet *errnum* einer Fehlermeldungszeichenfolge zu und gibt die Zeichenfolge im *Puffer*zurück. **_strerror_s** nimmt nicht die Fehlernummer; Es verwendet den aktuellen Wert von **errno,** um die entsprechende Nachricht zu bestimmen. Weder **strerror_s** noch **_strerror_s** die Meldung tatsächlich aus: Dazu müssen Sie eine Ausgabefunktion wie [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)aufrufen:

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Wenn *strErrMsg* **NULL**ist, **gibt _strerror_s** eine Zeichenfolge im *Puffer* zurück, die die Systemfehlermeldung für den letzten Bibliotheksaufruf enthält, der einen Fehler verursacht hat. Die Fehlermeldungszeichenfolge wird durch das Zeilenumbruchzeichen ('\n') beendet. Wenn *strErrMsg* nicht gleich **NULL**ist, gibt **_strerror_s** eine Zeichenfolge im *Puffer* zurück, die (in der Reihenfolge) Ihre Zeichenfolgennachricht, einen Doppelpunkt, ein Leerzeichen, die Systemfehlermeldung für den letzten Bibliotheksaufruf, der einen Fehler erzeugt, und ein Zeilenumlistenzeichen enthält. Die Zeichenfolgenmeldung darf höchstens 94 Zeichen lang sein.

Diese Funktionen abschneiden die Fehlermeldung, wenn ihre Länge *numberOfElements* -1 überschreitet. Die resultierende Zeichenfolge im *Puffer* ist immer null-beendet.

Die tatsächliche Fehlernummer für **_strerror_s** wird in der Variablen [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)gespeichert. Über die Variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) wird auf die Systemfehlermeldungen zugegriffen, die als Array von Meldungen nach Fehlernummern geordnet sind. **_strerror_s** greift auf die entsprechende Fehlermeldung zu, indem der **errno-Wert** als Index für die Variable **_sys_errlist**verwendet wird. Der Wert der Variablen [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ist definiert als die maximale Anzahl von Elementen im **array _sys_errlist.** Um genaue Ergebnisse zu erzielen, rufen **Sie _strerror_s** sofort auf, nachdem eine Bibliotheksroutine mit einem Fehler zurückgegeben wurde. Andernfalls können nachfolgende Aufrufe **von strerror_s** oder **_strerror_s** den **Errnowert** überschreiben.

**_wcserror_s** und **__wcserror_s** sind breitgefächerte Versionen von **strerror_s** bzw. **_strerror_s.**

Diese Funktionen überprüfen ihre Parameter. Wenn Buffer **NULL** ist oder wenn der Größenparameter 0 ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben die Funktionen **EINVAL** zurück und setzen **errno** auf **EINVAL**.

**_strerror_s** **, _wcserror_s**und **__wcserror_s** sind nicht Teil der ANSI-Definition, sondern Microsoft-Erweiterungen. Verwenden Sie sie nicht dort, wo Portabilität gewünscht wird; für ANSI-Kompatibilität, verwenden Sie **stattdessen strerror_s.**

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s**, **__wcserror_s**|\<string.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Betrachten Sie das Beispiel für [perror](perror-wperror.md).

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
