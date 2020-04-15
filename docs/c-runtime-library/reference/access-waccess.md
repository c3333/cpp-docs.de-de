---
title: _access, _waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: 98726726e14aacec75ed99adfa33016b40affd17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350874"
---
# <a name="_access-_waccess"></a>_access, _waccess

Legt fest, ob eine Datei schreibgeschützt ist. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_access_s, waccess_s](access-s-waccess-s.md).

## <a name="syntax"></a>Syntax

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parameter

*path*<br/>
Datei oder Verzeichnispfad.

*Modus*<br/>
Lese-/Schreibattribut.

## <a name="return-value"></a>Rückgabewert

Jede Funktion gibt 0 zurück, wenn sich die Datei im angegebenen Modus befindet. Die Funktion gibt -1 zurück, wenn die benannte Datei nicht vorhanden ist oder nicht über den angegebenen Modus verfügt. in diesem `errno` Fall, wird wie in der folgenden Tabelle dargestellt festgelegt.

|||
|-|-|
`EACCES`|Zugriff verweigert: Aufgrund der Berechtigungen wird der Zugriff im angegebenen Modus verweigert.
`ENOENT`|Der Dateiname oder der Pfad wurde nicht gefunden.
`EINVAL`|Ungültiger Parameter.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Bei Verwendung mit Dateien bestimmt die **_access-Funktion,** ob die angegebene Datei oder das angegebene Verzeichnis vorhanden ist, und weist die Attribute auf, die durch den Wert von *mode*angegeben sind. Bei Verwendung mit Verzeichnissen **bestimmt _access** nur, ob das angegebene Verzeichnis vorhanden ist. In Windows 2000 und neueren Betriebssystemen verfügen alle Verzeichnisse über Lese- und Schreibzugriff.

|*Moduswert*|überprüft nur, ob die Datei|
|------------------|---------------------|
|00|existiert|
|02|Nur Schreibzugriff|
|04|Schreibgeschützt|
|06|Lesen und Schreiben|

Diese Funktion überprüft nur, ob die Datei oder das Verzeichnis schreibgeschützt sind. Es überprüft jedoch nicht die Dateisystem-Sicherheitseinstellungen. Dafür benötigen Sie ein Zugriffstoken. Weitere Informationen zur Dateisystemsicherheit finden Sie unter [Zugriffstoken](/windows/win32/SecAuthZ/access-tokens). Für diese Funktion gibt es eine ATL-Klasse. Weitere Informationen finden Sie unter [CAccessToken-Klasse](../../atl/reference/caccesstoken-class.md).

**_waccess** ist eine breit gefächerte Version von **_access**; Das *Pfadargument* zu **_waccess** ist eine Zeichenfolge mit großen Zeichen. **_waccess** und **_access** verhalten sich ansonsten gleich.

Diese Funktion überprüft ihre Parameter. Wenn *Pfad* NULL ist oder *der Modus* keinen gültigen Modus angibt, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, legt die Funktion `errno` auf `EINVAL` fest und gibt –1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> oder \<io.h>|\<errno.h>|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird **_access** verwendet, um die Datei mit dem Namen crt_ACCESS zu überprüfen. C, um zu sehen, ob es existiert und ob Schreiben erlaubt ist.

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat-Funktionen](stat-functions.md)
