---
title: _searchenv, _wsearchenv
ms.date: 4/2/2020
api_name:
- _searchenv
- _wsearchenv
- _o__searchenv
- _o__wsearchenv
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: 22a8ca8fa7e56a84289d7e90ffb519073f006b5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332384"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Verwendet Umgebungspfade für die Suche nach einer Datei. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Der Name der zu suchenden Datei.

*Varname*<br/>
Zu durchsuchende Umgebung.

*Pfadnamen*<br/>
Puffer zum Speichern des vollständigen Pfades.

## <a name="remarks"></a>Bemerkungen

Die **_searchenv-Routine** sucht nach der Zieldatei in der angegebenen Domäne. Die *varname-Variable* kann eine beliebige Umgebung oder benutzerdefinierte Variable sein, z. B. **PATH**, **LIB**oder **INCLUDE**–, die eine Liste von Verzeichnispfaden angibt. Da **_searchenv** groß ist, sollte *varname* mit der Groß-/Kleinschreibung der Umgebungsvariablen übereinstimmen.

Die Routine sucht zuerst im aktuellen Arbeitsverzeichnis nach der Datei. Wenn die Datei dort nicht gefunden wird, werden die in der Umgebungsvariablen angegebenen Verzeichnisse durchsucht. Wenn sich die Zieldatei in einem dieser Verzeichnisse befindet, wird der neu erstellte Pfad in *den Pfadnamen*kopiert. Wenn die *Dateinamedatei* nicht gefunden wird, enthält *pathname* eine leere null-terminierte Zeichenfolge.

Der *Pfadnamenpuffer* sollte mindestens **_MAX_PATH** Zeichen lang sein, um die gesamte Länge des erstellten Pfadnamens aufzunehmen. Andernfalls **_searchenv** den *Pfadnamenpuffer* überlaufen und unerwartetes Verhalten verursachen.

**_wsearchenv** ist eine breitstellige Version von **_searchenv**, und die Argumente für **_wsearchenv** sind Zeichenfolgen mit großen Zeichen. **_wsearchenv** und **_searchenv** verhalten sich ansonsten gleich.

Wenn *filename* eine leere Zeichenfolge ist, geben diese Funktionen **ENOENT**zurück.

Wenn *filename* oder *pathname* ein **NULL-Zeiger** ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen -1 zurück und setzen **errno** auf **EINVAL**.

Weitere Informationen zu **Errno-** und Fehlercodes finden Sie unter [errno Constants](../../c-runtime-library/errno-constants.md).

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Siehe auch

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
