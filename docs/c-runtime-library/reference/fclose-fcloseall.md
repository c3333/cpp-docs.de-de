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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347492"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Schließt einen Stream (**fclose**) oder schließt alle offenen Streams (**_fcloseall**).

## <a name="syntax"></a>Syntax

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parameter

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

**fclose** gibt 0 zurück, wenn der Stream erfolgreich geschlossen wurde. **_fcloseall** gibt die Gesamtzahl der geschlossenen Streams zurück. Beide Funktionen geben **EOF** zurück, um einen Fehler anzuzeigen.

## <a name="remarks"></a>Bemerkungen

Die **fclose-Funktion** schließt *den Stream*. Wenn *Der Stream* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt **fclose** **errno** auf **EINVAL** und gibt **EOF**zurück. Es wird empfohlen, den *Streamzeiger* immer vor dem Aufruf dieser Funktion zu überprüfen.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Die **_fcloseall-Funktion** schließt alle offenen Streams außer **stdin**, **stdout**, **stderr** (und in MS-DOS, **_stdaux** und **_stdprn**). Außerdem werden alle temporären Dateien geschlossen und gelöscht, die von **tmpfile**erstellt wurden. Bei beiden Funktionen werden alle Puffer, die dem Stream zugewiesen sind, vor dem Schließen geleert. Systemseitig angegebene Puffer werden freigegeben, wenn der Stream geschlossen wird. Puffer, die vom Benutzer mit **setbuf** und **setvbuf** zugewiesen werden, werden nicht automatisch freigegeben.

**Hinweis:** Wenn diese Funktionen verwendet werden, um einen Stream zu schließen, werden ebenso wie der Stream auch der zugrundeliegende Dateideskriptor und das Dateihandle des Betriebssystems geschlossen. Wenn die Datei also ursprünglich als Dateihandle oder Dateideskriptor geöffnet wurde und mit **fclose**geschlossen wird, rufen Sie nicht auch **_close** auf, um den Dateideskriptor zu schließen. Rufen Sie nicht die Win32-Funktion **CloseHandle** auf, um das Dateihandle zu schließen.

**fclose** und **_fcloseall** Code enthalten, um vor Interferenzen durch andere Threads zu schützen. Informationen zur nicht sperrenden Version eines **fclose**finden Sie **unter _fclose_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [open](fopen-wfopen.md).

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
