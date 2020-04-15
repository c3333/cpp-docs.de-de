---
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341602"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Erstellt einen Pfadnamen aus Komponenten Dies sind Versionen von [_makepath, _wmakepath](makepath-wmakepath.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>Parameter

*path*<br/>
Vollständiger Pfadpuffer

*sizeInWords*<br/>
Größe des Puffers in Worten

*sizeInBytes*<br/>
Größe des Puffers in Byte.

*Laufwerk*<br/>
Enthält einen Buchstaben (A, B usw.) für das gewünschte Laufwerk und einen optionalen nachgestellten Doppelpunkt. **_makepath_s** fügt den Doppelpunkt automatisch in den zusammengesetzten Pfad ein, wenn er fehlt. Wenn *das Laufwerk* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird in der zusammengesetzten *Pfadzeichenfolge* kein Laufwerkbuchstabe angezeigt.

*dir*<br/>
Enthält den Pfad der Verzeichnisse, ausgenommen die Laufwerkkennzeichner oder den tatsächlichen Dateinamen. Der nachfolgende Schrägstrich ist optional, und entweder ein Schrägstrich (/) oder ein umgekehrter Schrägstrich (\\) oder beides kann in einem einzelnen *dir-Argument* verwendet werden. Wenn kein nachstehender Schrägstrich (/ oder \\) angegeben ist, wird er automatisch eingefügt. Wenn *dir* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird kein Verzeichnispfad in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

*Fname*<br/>
Enthält den Basisdateinamen ohne Dateinamenerweiterungen. Wenn *fname* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird kein Dateiname in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

*Extern*<br/>
Enthält die eigentliche Dateinamenerweiterung mit oder ohne führenden Punkt (.). **_makepath_s** fügt die Periode automatisch ein, wenn sie nicht in *ext*angezeigt wird. Wenn *ext* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird keine Erweiterung in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*path*|*sizeInWords* / *sizeInBytes*|Rückgabewert|Inhalt des *Pfades*|
|------------|------------------------------------|------------|------------------------|
|**Null**|any|**Einval**|nicht geändert|
|any|<= 0|**Einval**|nicht geändert|

Wenn Fehlerzustände wie die oben genannten auftreten, wird ein Handler für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktionen geben **EINVAL**zurück. **NULL** ist für die Parameter *Drive*, *fname*und *ext*zulässig. Informationen zum Verhalten, wenn es sich bei diesen Parametern um NULL-Zeiger oder leere Zeichenfolgen handelt, finden Sie im Abschnitt Hinweise.

## <a name="remarks"></a>Bemerkungen

Die **_makepath_s-Funktion** erstellt eine zusammengesetzte Pfadzeichenfolge aus einzelnen Komponenten, die das Ergebnis im *Pfad*speichert. Der *Pfad* kann einen Laufwerkbuchstaben, einen Verzeichnispfad, einen Dateinamen und eine Dateinamenerweiterung enthalten. **_wmakepath_s** ist eine breit **gefächerte**Version von _makepath_s ; Die Argumente für **_wmakepath_s** sind Zeichenfolgen mit großen Zeichen. **_wmakepath_s** und **_makepath_s** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Das *Pfadargument* muss auf einen leeren Puffer verweisen, der groß genug ist, um den vollständigen Pfad zu halten. Der zusammengesetzte *Pfad* darf nicht größer sein als die **_MAX_PATH** konstante, die in Stdlib.h definiert ist.

Wenn pfad **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Darüber hinaus ist **errno** auf **EINVAL**gesetzt. **NULL-Werte** sind für alle anderen Parameter zulässig.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
