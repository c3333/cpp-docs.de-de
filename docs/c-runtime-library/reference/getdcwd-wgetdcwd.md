---
title: _getdcwd, _wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 69e9d0b0eaa3a62d95ea602b68b5d1ad0df99e4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919220"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd, _wgetdcwd

Ruft den vollständigen Pfad des aktuellen Arbeitsverzeichnisses auf dem angegebenen Laufwerk ab.

## <a name="syntax"></a>Syntax

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parameter

*Antrie*<br/>
Eine nicht negative ganze Zahl, die das Laufwerk angibt (0 = Standardlaufwerk, 1 = A, 2 = B usw.).

Wenn das angegebene Laufwerk nicht verfügbar ist oder die Art des Laufwerks (z. b. Wechsel Datenträger, Festplattenlaufwerke, CD-ROM, RAM-Datenträger oder Netzlaufwerk) nicht bestimmt werden kann, wird der Handler für ungültige Parameter aufgerufen. Weitere Informationen finden Sie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md).

*ert*<br/>
Speicherort für den Pfad, oder **NULL**.

Wenn **null** angegeben wird, weist diese Funktion einen Puffer mit einer Größe von mindestens *maxlen* mithilfe von **malloc**zu, und der Rückgabewert von **_getdcwd** ist ein Zeiger auf den zugeordneten Puffer. Der Puffer kann freigegeben werden, **indem aufgerufen und** der Zeiger übergeben wird.

*maxlen*<br/>
Eine positive ganze Zahl ungleich NULL, die die maximale Länge des Pfads angibt, in Zeichen: **char** für **_getdcwd** und **wchar_t** für **_wgetdcwd**.

Wenn *maxlen* kleiner oder gleich 0 (null) ist, wird der Handler für ungültige Parameter aufgerufen. Weitere Informationen finden Sie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md).

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den vollständigen Pfad des aktuellen Arbeitsverzeichnisses auf dem angegebenen Laufwerk darstellt, oder **null**, was auf einen Fehler hinweist.

Wenn *buffer* als **null** angegeben ist und nicht genügend Arbeitsspeicher zum Zuordnen von *maxlen* -Zeichen vorhanden ist, tritt ein Fehler auf, und **errno** ist auf **ENOMEM**festgelegt. Wenn die Länge des Pfads einschließlich des abschließenden NULL-Zeichens *maxlen*überschreitet, tritt ein Fehler auf, und **errno** ist auf **ERANGE**festgelegt. Weitere Informationen zu diesen Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_getdcwd** -Funktion Ruft den vollständigen Pfad des aktuellen Arbeitsverzeichnisses auf dem angegebenen Laufwerk ab und speichert Sie im *Puffer*. Wenn das aktuelle Arbeitsverzeichnis auf das Stammverzeichnis festgelegt ist, endet die Zeichenfolge mit einem umgekehrten Schrägstrich (\\). Wenn das aktuelle Arbeitsverzeichnis nicht auf das Stammverzeichnis festgelegt ist, endet die Zeichenfolge mit dem Namen des Verzeichnisses und nicht mit einem umgekehrten Schrägstrich.

**_wgetdcwd** ist eine breit Zeichen Version von **_getdcwd**, und der *Puffer* Parameter und der Rückgabewert sind Zeichen folgen mit breit Zeichen. Andernfalls Verhalten sich **_wgetdcwd** und **_getdcwd** identisch.

Diese Funktion ist threadsicher, obwohl sie von der Funktion **GetFullPathName**abhängig ist, die selbst nicht threadsicher ist. Es kann jedoch zu einer Verletzung der Threadsicherheit kommen, wenn die Multithreadanwendung sowohl diese Funktion als auch [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)aufruft.

Die Version dieser Funktion mit dem **_nolock** -Suffix verhält sich identisch mit dieser Funktion, mit der Ausnahme, dass Sie nicht Thread sicher ist und nicht vor Störungen durch andere Threads geschützt ist. Weitere Informationen finden Sie unter [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md).

Wenn **_DEBUG** und **_CRTDBG_MAP_ALLOC** definiert sind, werden Aufrufe von **_getdcwd** und **_wgetdcwd** durch Aufrufe von **_getdcwd_dbg** und **_wgetdcwd_dbg** ersetzt, sodass Sie Speicher Belegungen Debuggen können. Weitere Informationen finden Sie unter[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel in [_getdrive](getdrive.md).

## <a name="see-also"></a>Weitere Informationen

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
