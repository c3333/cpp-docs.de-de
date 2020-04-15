---
title: _makepath, _wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341592"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

Erstellen Sie einen Pfadnamen aus Komponenten. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="syntax"></a>Syntax

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>Parameter

*path*<br/>
Vollständiger Pfadpuffer

*Laufwerk*<br/>
Enthält einen Buchstaben (A, B usw.) für das gewünschte Laufwerk und einen optionalen nachgestellten Doppelpunkt. **_makepath** fügt den Doppelpunkt automatisch in den zusammengesetzten Pfad ein, wenn er fehlt. Wenn *das Laufwerk* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird in der zusammengesetzten *Pfadzeichenfolge* kein Laufwerkbuchstabe angezeigt.

*dir*<br/>
Enthält den Pfad der Verzeichnisse, ausgenommen die Laufwerkkennzeichner oder den tatsächlichen Dateinamen. Der nachfolgende Schrägstrich ist optional, und entweder ein Schrägstrich (/) oder ein umgekehrter Schrägstrich (\\) oder beides kann in einem einzelnen *dir-Argument* verwendet werden. Wenn kein nachstehender Schrägstrich (/ oder \\) angegeben ist, wird er automatisch eingefügt. Wenn *dir* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird kein Verzeichnispfad in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

*Fname*<br/>
Enthält den Basisdateinamen ohne Dateinamenerweiterungen. Wenn *fname* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird kein Dateiname in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

*Extern*<br/>
Enthält die eigentliche Dateinamenerweiterung mit oder ohne führenden Punkt (.). **_makepath** fügt die Periode automatisch ein, wenn sie nicht in *ext*angezeigt wird. Wenn *ext* **NULL** ist oder auf eine leere Zeichenfolge zeigt, wird keine Erweiterung in die zusammengesetzte *Pfadzeichenfolge* eingefügt.

## <a name="remarks"></a>Bemerkungen

Die **_makepath-Funktion** erstellt eine zusammengesetzte Pfadzeichenfolge aus einzelnen Komponenten, die das Ergebnis im *Pfad*speichert. Der *Pfad* kann einen Laufwerkbuchstaben, einen Verzeichnispfad, einen Dateinamen und eine Dateinamenerweiterung enthalten. **_wmakepath** ist eine breit **gefächerte**Version von _makepath ; Die Argumente für **_wmakepath** sind Zeichenfolgen mit großen Zeichen. **_wmakepath** und **_makepath** verhalten sich ansonsten gleich.

**Sicherheitshinweis** Verwenden Sie eine mit NULL endende Zeichenfolge. Um einen Pufferüberlauf zu vermeiden, darf die null-terminierte Zeichenfolge die Größe des *Pfadpuffers* nicht überschreiten. **_makepath** stellt nicht sicher, dass die Länge der zusammengesetzten Pfadzeichenfolge **_MAX_PATH**nicht überschreitet. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Das *Pfadargument* muss auf einen leeren Puffer verweisen, der groß genug ist, um den vollständigen Pfad zu halten. Der zusammengesetzte *Pfad* darf nicht größer sein als die **_MAX_PATH** konstante, die in Stdlib.h definiert ist.

Wenn pfad **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Darüber hinaus ist **errno** auf **EINVAL**gesetzt. **NULL-Werte** sind für alle anderen Parameter zulässig.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
