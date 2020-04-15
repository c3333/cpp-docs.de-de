---
title: _chdir, _wchdir
ms.date: 4/2/2020
api_name:
- _wchdir
- _chdir
- _o__chdir
- _o__wchdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
ms.openlocfilehash: a3f224e68e4b5a43274616892012ceba737d6d17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333389"
---
# <a name="_chdir-_wchdir"></a>_chdir, _wchdir

Ändert das aktuelle Arbeitsverzeichnis.

## <a name="syntax"></a>Syntax

```C
int _chdir(
   const char *dirname
);
int _wchdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parameter

*Dirname*<br/>
Pfad des neuen Arbeitsverzeichnisses.

## <a name="return-value"></a>Rückgabewert

Diese Funktionen geben bei Erfolg den Wert 0 zurück. Ein Rückgabewert von -1 gibt einen Fehler an. Wenn der angegebene Pfad nicht gefunden werden konnte, wird **errno** auf **ENOENT**festgelegt. Wenn *dirname* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktion gibt -1 zurück.

## <a name="remarks"></a>Bemerkungen

Die **Funktion _chdir** ändert das aktuelle Arbeitsverzeichnis in das von *dirname*angegebene Verzeichnis. Der *Parameter dirname* muss auf ein vorhandenes Verzeichnis verweisen. Diese Funktion kann das aktuelle Arbeitsverzeichnis auf jedem beliebigen Laufwerk ändern. Wenn ein neuer Laufwerkbuchstabe in *dirname*angegeben wird, wird auch der Standardlaufwerkbuchstabe geändert. Wenn z. B. A der Standardlaufwerkbuchstabe und \BIN das aktuelle Arbeitsverzeichnis ist, ändert der folgende Aufruf das aktuelle Arbeitsverzeichnis in C und legt C als neues Standardlaufwerk fest:

```C
_chdir("c:\temp");
```

Wenn Sie das optionale umgekehrte Schrägstrichzeichen (**&#92;**) in Pfaden verwenden, müssen Sie zwei umgekehrte Schrägstriche (**&#92;&#92;**) in einem C-Zeichenfolgenliteral platzieren, um einen einzelnen umgekehrten Schrägstrich darzustellen (**&#92;**).

**_wchdir** ist eine breit **gefächerte**Version von _chdir ; Das *dirname-Argument* für **_wchdir** ist eine Zeichenfolge mit großen Zeichen. **_wchdir** und **_chdir** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Zuordnung generischer Textroutinen:

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_chdir**|\<direct.h>|\<errno.h>|
|**_wchdir**|\<direct.h> oder \<wchar.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_chdir.c
// arguments: C:\WINDOWS

/* This program uses the _chdir function to verify
   that a given directory exists. */

#include <direct.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int argc, char *argv[] )
{

   if(_chdir( argv[1] ) )
   {
      switch (errno)
      {
      case ENOENT:
         printf( "Unable to locate the directory: %s\n", argv[1] );
         break;
      case EINVAL:
         printf( "Invalid buffer.\n");
         break;
      default:
         printf( "Unknown error.\n");
      }
   }
   else
      system( "dir *.exe");
}
```

```Output
Volume in drive C has no label.
Volume Serial Number is 2018-08A1

Directory of c:\windows

08/29/2002  04:00 AM         1,004,032 explorer.exe
12/17/2002  04:43 PM            10,752 hh.exe
03/03/2003  09:24 AM            33,792 ieuninst.exe
10/29/1998  04:45 PM           306,688 IsUninst.exe
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE
03/03/2003  09:24 AM            33,792 Q330994.exe
08/29/2002  04:00 AM           134,144 regedit.exe
02/28/2003  06:26 PM            46,352 setdebug.exe
08/29/2002  04:00 AM            15,360 TASKMAN.EXE
08/29/2002  04:00 AM            49,680 twunk_16.exe
08/29/2002  04:00 AM            25,600 twunk_32.exe
08/29/2002  04:00 AM           256,192 winhelp.exe
08/29/2002  04:00 AM           266,752 winhlp32.exe
              13 File(s)      2,249,184 bytes
               0 Dir(s)  67,326,029,824 bytes free
```

## <a name="see-also"></a>Siehe auch

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
