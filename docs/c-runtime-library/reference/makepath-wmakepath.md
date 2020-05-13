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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 19a20de40bb02e49f618e8e617c9659788dc3e25
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914393"
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

*Antrie*<br/>
Enthält einen Buchstaben (A, B usw.) für das gewünschte Laufwerk und einen optionalen nachgestellten Doppelpunkt. **_makepath** fügt den Doppelpunkt automatisch in den zusammengesetzten Pfad ein, wenn dieser nicht vorhanden ist. Wenn *drive* das Laufwerk **null** ist oder auf eine leere Zeichenfolge verweist, wird kein Laufwerk Buchstabe in der Zeichenfolge für den zusammengesetzten *Pfad* angezeigt.

*dir*<br/>
Enthält den Pfad der Verzeichnisse, ausgenommen die Laufwerkkennzeichner oder den tatsächlichen Dateinamen. Der nachstehende Schrägstrich ist optional, und entweder ein Schrägstrich (/) oder ein umgekehrter Schrägstrich (\\) oder beides kann in einem einzelnen *dir* -Argument verwendet werden. Wenn kein nachstehender Schrägstrich (/ oder \\) angegeben ist, wird er automatisch eingefügt. Wenn *dir* **null** ist oder auf eine leere Zeichenfolge verweist, wird kein Verzeichnispfad in die zusammengesetzte *Pfad* Zeichenfolge eingefügt.

*fname*<br/>
Enthält den Basisdateinamen ohne Dateinamenerweiterungen. Wenn *fname* **null** ist oder auf eine leere Zeichenfolge verweist, wird kein Dateiname in die zusammengesetzte *Pfad* Zeichenfolge eingefügt.

*Antrags*<br/>
Enthält die eigentliche Dateinamenerweiterung mit oder ohne führenden Punkt (.). **_makepath** fügt den Zeitraum automatisch ein, wenn er nicht in *ext*angezeigt wird. Wenn *ext* **null** ist oder auf eine leere Zeichenfolge zeigt, wird keine Erweiterung in die zusammengesetzte *Pfad* Zeichenfolge eingefügt.

## <a name="remarks"></a>Hinweise

Die **_makepath** -Funktion erstellt eine zusammengesetzte Pfad Zeichenfolge aus einzelnen Komponenten und speichert das Ergebnis im *Pfad*. Der *Pfad* kann einen Laufwerk Buchstaben, einen Verzeichnispfad, einen Dateinamen und eine Dateinamenerweiterung enthalten. **_wmakepath** ist eine breit Zeichen Version von **_makepath**. die Argumente für **_wmakepath** sind Zeichen folgen mit breit Zeichen. **_wmakepath** und **_makepath** Verhalten sich andernfalls identisch.

**Sicherheitshinweis** Verwenden Sie eine mit NULL endende Zeichenfolge. Um einen Pufferüberlauf zu vermeiden, darf die mit NULL endenden Zeichenfolge die Größe des *Pfad* Puffers nicht überschreiten. **_makepath** stellt nicht sicher, dass die Länge der zusammengesetzten Pfad Zeichenfolge **_MAX_PATH**nicht überschreitet. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Das *path* -Argument muss auf einen leeren Puffer zeigen, der groß genug ist, um den gesamten Pfad zu speichern. Der zusammengesetzte *Pfad* darf nicht größer als die **_MAX_PATH** Konstante sein, die in "STDLIB. h" definiert ist.

Wenn path **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Außerdem wird **errno** auf **EINVAL**festgelegt. **Null** -Werte sind für alle anderen Parameter zulässig.

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

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
