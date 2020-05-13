---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 3f8567f7bb01c519938f5a4e28bbb33bce09dffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920227"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Schließt einen Stream (**sClose**) oder schließt alle geöffneten Streams (**_fcloseall**).

## <a name="syntax"></a>Syntax

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

" **f** " gibt 0 zurück, wenn der Stream erfolgreich geschlossen wurde. **_fcloseall** gibt die Gesamtzahl der geschlossenen Streams zurück. Beide Funktionen geben **EOF** zurück, um einen Fehler anzugeben.

## <a name="remarks"></a>Hinweise

Die Funktion " **sClose** " schließt den Daten *Strom*. Wenn *stream* der Stream **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** von **fclose** auf **EINVAL** festgelegt und **EOF**zurückgegeben. Es wird empfohlen, den *Streamzeiger* vor dem Aufrufen dieser Funktion immer zu überprüfen.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Die **_fcloseall** -Funktion schließt alle geöffneten Streams außer **stdin**, **stdout**, **stderr** (und in MS-DOS, **_stdaux** und **_stdprn**). Außerdem werden alle temporären Dateien, die von **tmpfile**erstellt werden, geschlossen und gelöscht. Bei beiden Funktionen werden alle Puffer, die dem Stream zugewiesen sind, vor dem Schließen geleert. Systemseitig angegebene Puffer werden freigegeben, wenn der Stream geschlossen wird. Puffer, die vom Benutzer mit **setbuf** und **setvbuf** zugewiesen werden, werden nicht automatisch freigegeben.

**Hinweis:** Wenn diese Funktionen verwendet werden, um einen Stream zu schließen, werden ebenso wie der Stream auch der zugrundeliegende Dateideskriptor und das Dateihandle des Betriebssystems geschlossen. Wenn die Datei ursprünglich als Datei Handle oder Dateideskriptor geöffnet wurde und mit **fclose**geschlossen wurde, wird nicht auch **_close** aufgerufen, um den Dateideskriptor zu schließen. die Win32-Funktion **CloseHandle** muss nicht aufgerufen werden, um das Datei Handle zu schließen.

**fclose** und **_fcloseall** enthalten Code zum Schutz vor Störungen durch andere Threads. Informationen zur nicht Sperr Version eines **sClose**finden Sie unter **_fclose_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [open](fopen-wfopen.md).

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
