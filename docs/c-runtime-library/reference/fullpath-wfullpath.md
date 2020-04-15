---
title: _fullpath, _wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345482"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath, _wfullpath

Erstellt einen absoluten oder vollständigen Pfadnamen für den angegebenen relativen Pfadnamen

## <a name="syntax"></a>Syntax

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>Parameter

*absPath*<br/>
Zeiger auf einen Puffer, der den absoluten oder vollständigen Pfadnamen oder **NULL**enthält.

*relPath*<br/>
Relativer Pfadname.

*maxLength*<br/>
Maximale Länge des absoluten Pfadnamenpuffers (*absPath*). Diese Länge ist in Bytes für **_fullpath,** aber in breiten Zeichen (**wchar_t**) für **_wfullpath**.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf einen Puffer zurück, der den absoluten Pfadnamen (*absPath*) enthält. Wenn ein Fehler vorliegt (z. B. wenn der in *relPath* übergebene Wert einen Laufwerkbuchstaben enthält, der ungültig ist oder nicht gefunden werden kann, oder wenn die Länge des erstellten absoluten Pfadnamens (*absPath*) größer als *maxLength*ist), gibt die Funktion **NULL**zurück.

## <a name="remarks"></a>Bemerkungen

Die **_fullpath-Funktion** erweitert den relativen Pfadnamen in *relPath* auf seinen vollqualifizierten oder absoluten Pfad und speichert diesen Namen in *absPath*. Wenn *absPath* **NULL**ist, wird **malloc** verwendet, um einen Puffer mit ausreichender Länge zuzuweisen, um den Pfadnamen zu halten. Der Aufrufer muss diesen Puffer freigeben. Dieser relative Pfadname gibt vom aktuellen Speicherort einen Pfad zu einem anderen Speicherort an (z.B. das aktuelle Arbeitsverzeichnis: "."). Ein absoluter Pfadname ist die Erweiterung eines relativen Pfadnamens, der den gesamten Pfad ausdrückt, der dafür erforderlich ist, um die gewünschte Position aus dem Stammverzeichnis des Dateisystems zu erreichen. Im Gegensatz zu **_makepath** **können _fullpath** verwendet werden, um den absoluten Pfadnamen für relative Pfade (*relPath*) zu erhalten, die "./" oder "." enthalten. /" in ihren Namen.

Um beispielsweise C-Laufzeitroutinen verwenden zu können, muss die Anwendung die Headerdateien enthalten, die die Deklarationen für die Routinen enthalten. Jede Headerdatei enthält Anweisungen, die relativ auf den Speicherort der Datei verweisen (aus dem Arbeitsverzeichnis der Anwendung):

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

Wenn der absolute Pfad (der tatsächliche Dateisystem-Speicherort) der Datei z.B. wie folgt lautet:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der derzeit in Gebrauch befindlichen Multibyte-Codepage erkannt werden. **_wfullpath** ist eine breit gefächerte Version von **_fullpath**; Die Zeichenfolgenargumente für **_wfullpath** sind Zeichenfolgen mit großen Zeichen. **_wfullpath** und **_fullpath** verhalten sich identisch, außer dass **_wfullpath** keine Zeichenfolgen mit mehreren Byte-Zeichen verarbeitet.

Wenn **_DEBUG** und **_CRTDBG_MAP_ALLOC** beide definiert sind, werden Aufrufe von **_fullpath** und **_wfullpath** durch Aufrufe **von _fullpath_dbg** ersetzt und **_wfullpath_dbg,** um Speicherzuweisungen zu debuggen. Weitere Informationen finden Sie unter [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Diese Funktion ruft den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben, wenn *maxlen* kleiner oder gleich 0 ist. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **NULL**zurück.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Wenn der *absPath-Puffer* **NULL**ist, **ruft _fullpath** [malloc](malloc.md) auf, einen Puffer zuzuweisen, und ignoriert das *argument maxLength.* Es liegt in der Verantwortung des Aufrufers, die Zuordnung für diesen Puffer richtig wieder aufzuheben (mithilfe von [free](free.md)). Wenn das *relPath-Argument* ein Laufwerk angibt, wird das aktuelle Verzeichnis dieses Laufwerks mit dem Pfad kombiniert.

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
