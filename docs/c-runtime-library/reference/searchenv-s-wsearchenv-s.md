---
title: _searchenv_s, _wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 5dd21013c8910ba07e2d23606af49bc80458dbc6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918994"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Sucht mithilfe von Umgebungspfaden nach einer Datei. Diese Versionen von [_searchenv, _wsearchenv](searchenv-wsearchenv.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*Einfügen*<br/>
Der Name der zu suchenden Datei.

*varname*<br/>
Zu durchsuchende Umgebung.

*Pfadnamen*<br/>
Puffer zum Speichern des vollständigen Pfades.

*numberOfElements*<br/>
Größe des *Pfadnamen* Puffers.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt.

Wenn *filename* eine leere Zeichenfolge ist, ist der Rückgabewert **ENOENT**.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Einfügen*|*varname*|*Pfadnamen*|*numberOfElements*|Rückgabewert|Inhalt von *Pfadnamen*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|any|any|**Normal**|any|**Eingabe**|–|
|**Normal**|any|any|any|**Eingabe**|nicht geändert|
|any|any|any|<= 0|**Eingabe**|nicht geändert|

Wenn eine dieser Fehlerbedingungen auftritt, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen " **errno** " auf " **EINVAL** " fest und geben " **EINVAL**" zurück.

## <a name="remarks"></a>Hinweise

Die **_searchenv_s** Routine sucht in der angegebenen Domäne nach der Zieldatei. Die *varname* -Variable kann eine beliebige Umgebung oder eine benutzerdefinierte Variable sein, die eine Liste von Verzeichnis Pfaden angibt, wie z. b. **path**, **lib**und **include**. Da bei **_searchenv_s** die Groß-/Kleinschreibung beachtet wird, sollte *varname* dem Fall der Umgebungsvariablen entsprechen. Wenn *varname* nicht mit dem Namen einer Umgebungsvariablen identisch ist, die in der Umgebung des Prozesses definiert ist, gibt die Funktion 0 (null) zurück, und die *Pfadname* -Variable bleibt unverändert.

Die Routine sucht zuerst im aktuellen Arbeitsverzeichnis nach der Datei. Wenn die Datei dort nicht gefunden wird, werden als Nächstes die in der Umgebungsvariablen angegebenen Verzeichnisse durchsucht. Wenn sich die Zieldatei in einem dieser Verzeichnisse befindet, wird der neu erstellte Pfad in *Pfadnamen*kopiert. Wenn die Datei *Namen* Datei nicht gefunden wird, enthält *Pfadnamen* eine leere NULL-terminierte Zeichenfolge.

Der *Pfadname* -Puffer muss mindestens **_MAX_PATH** Zeichen lang sein, um die vollständige Länge des erstellten Pfadnamens zu berücksichtigen. Andernfalls können **_searchenv_s** den *Pfadnamen* -Puffer überlaufen, was zu unerwartetem Verhalten führt.

**_wsearchenv_s** ist eine breit Zeichen Version von **_searchenv_s**. die Argumente für **_wsearchenv_s** sind Zeichen folgen mit breit Zeichen. **_wsearchenv_s** und **_searchenv_s** Verhalten sich andernfalls identisch.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Weitere Informationen

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
