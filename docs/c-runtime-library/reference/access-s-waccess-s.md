---
title: _access_s, _waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: c3893b3d78a2c142ffc9e10eb6bbf299c5fddb9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916897"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Bestimmt die Lese-/Schreibberechtigungen einer Datei. Dies ist eine sicherere Version von [_access, _waccess](access-waccess.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parameter

*path*<br/>
Datei oder Verzeichnispfad.

*mode*<br/>
Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Jede Funktion gibt 0 zurück, wenn sich die Datei im angegebenen Modus befindet. Die Funktion gibt einen Fehlercode zurück, wenn die angegebene Datei nicht vorhanden ist oder im angegebenen Modus nicht auf sie zugegriffen werden kann. In diesem Fall gibt die Funktion einen Fehlercode zurück und legt `errno` auf diesen Code fest.

|errno-Wert|Bedingung|
|-|-|
`EACCES`|Der Zugriff wurde verweigert. Aufgrund der Berechtigungen wird der Zugriff im angegebenen Modus verweigert.
`ENOENT`|Der Dateiname oder der Pfad wurde nicht gefunden.
`EINVAL`|Ungültiger Parameter.

Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Bei Verwendung mit-Dateien bestimmt die **_access_s** Funktion, ob die angegebene Datei vorhanden ist und wie im Wert des- *Modus*angegeben auf Sie zugegriffen werden kann. Bei der Verwendung mit Verzeichnissen bestimmt **_access_s** nur, ob das angegebene Verzeichnis vorhanden ist. In Windows 2000 und neueren Betriebssystemen haben alle Verzeichnisse Lese-und Schreibzugriff.

|Moduswert|überprüft nur, ob die Datei|
|----------------|---------------------|
|00|existiert.|
|02|Schreibberechtigung.|
|04|Leseberechtigung.|
|06|Lese- und Schreibberechtigung.|

Die Berechtigung zum Lesen oder Schreiben einer Datei garantiert nicht, dass diese Datei auch geöffnet werden kann. Wenn eine Datei z. b. von einem anderen Prozess gesperrt ist, ist Sie möglicherweise nicht verfügbar, obwohl **_access_s** 0 zurückgibt.

**_waccess_s** ist eine breit Zeichen Version von **_access_s**, bei der das *Pfad* Argument für **_waccess_s** eine Zeichenfolge mit breit Zeichen ist. Andernfalls Verhalten sich **_waccess_s** und **_access_s** identisch.

Diese Funktionen überprüfen ihre Parameter. Wenn der *Pfad* NULL ist oder der *Modus* keinen gültigen Modus angibt, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, stellen diese Funktionen `errno` auf `EINVAL` ein und geben `EINVAL` zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> oder \<io.h>|\<errno.h>|

## <a name="example"></a>Beispiel

In diesem Beispiel wird **_access_s** verwendet, um die Datei crt_access_s. c zu überprüfen, um festzustellen, ob Sie vorhanden ist und ob Schreibvorgänge zulässig sind.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat-Funktionen](stat-functions.md)
