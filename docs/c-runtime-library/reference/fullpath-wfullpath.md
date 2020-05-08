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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f7ef9e8416e73a403abfb30f637afeb4a68e8592
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909941"
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

*abspath*<br/>
Zeiger auf einen Puffer, der den absoluten oder vollständigen Pfadnamen enthält, oder **null**.

*RelPath*<br/>
Relativer Pfadname.

*maxLength*<br/>
Maximale Länge des absoluten Pfadnamen Puffers (*abspath*). Diese Länge ist in Bytes für **_fullpath** , aber in breit Zeichen (**wchar_t**) für **_wfullpath**.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf einen Puffer zurück, der den absoluten Pfadnamen (*abspath*) enthält. Wenn ein Fehler vorliegt (z. b. wenn der in *RelPath* übergebenen Wert einen Laufwerk Buchstaben enthält, der nicht gültig ist oder nicht gefunden werden kann, oder wenn die Länge des erstellten absoluten Pfadnamens (*abspath*) größer als *MaxLength*ist), gibt die Funktion **null**zurück.

## <a name="remarks"></a>Hinweise

Die **_fullpath** -Funktion erweitert den relativen Pfadnamen in *RelPath* auf den voll qualifizierten oder absoluten Pfad und speichert diesen Namen in *abspath*. Wenn *abspath* **null**ist, wird **malloc** verwendet, um einen Puffer mit ausreichender Länge für den Pfadnamen zuzuweisen. Der Aufrufer muss diesen Puffer freigeben. Dieser relative Pfadname gibt vom aktuellen Speicherort einen Pfad zu einem anderen Speicherort an (z.B. das aktuelle Arbeitsverzeichnis: "."). Ein absoluter Pfadname ist die Erweiterung eines relativen Pfadnamens, der den gesamten Pfad ausdrückt, der dafür erforderlich ist, um die gewünschte Position aus dem Stammverzeichnis des Dateisystems zu erreichen. Im Gegensatz zu **_makepath**können **_fullpath** verwendet werden, um den absoluten Pfadnamen für relative Pfade (*RelPath*) zu erhalten, die "./" oder "." enthalten. /"in ihren Namen.

Um beispielsweise C-Laufzeitroutinen verwenden zu können, muss die Anwendung die Headerdateien enthalten, die die Deklarationen für die Routinen enthalten. Jede Headerdatei enthält Anweisungen, die relativ auf den Speicherort der Datei verweisen (aus dem Arbeitsverzeichnis der Anwendung):

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

Wenn der absolute Pfad (der tatsächliche Dateisystem-Speicherort) der Datei z.B. wie folgt lautet:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** automatisch Multibytezeichen-Zeichen folgen Argumente behandelt, wobei Multibytezeichen-Zeichensequenzen gemäß der derzeit verwendeten Multibytezeichen-Codepage erkannt werden. **_wfullpath** ist eine breit Zeichen Version von **_fullpath**. die Zeichen folgen Argumente für **_wfullpath** sind Zeichen folgen mit breit Zeichen. **_wfullpath** und **_fullpath** Verhalten sich identisch, mit dem Unterschied, dass **_wfullpath** keine Multibyte-Zeichen folgen verarbeitet.

Wenn sowohl **_DEBUG** als auch **_CRTDBG_MAP_ALLOC** definiert sind, werden Aufrufe von **_fullpath** und **_wfullpath** durch Aufrufe von **_fullpath_dbg** und **_wfullpath_dbg** ersetzt, um das Debuggen von Speicher Belegungen zuzulassen. Weitere Informationen finden Sie unter [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Diese Funktion Ruft den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben, wenn *maxlen* kleiner oder gleich 0 ist. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt **null**zurück.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Wenn der *abspath* -Puffer **null**ist, ruft **_fullpath** [malloc](malloc.md) auf, um einen Puffer zuzuordnen, und ignoriert das *MaxLength* -Argument. Es liegt in der Verantwortung des Aufrufers, die Zuordnung für diesen Puffer richtig wieder aufzuheben (mithilfe von [free](free.md)). Wenn das *RelPath* -Argument ein Laufwerk angibt, wird das aktuelle Verzeichnis dieses Laufwerks mit dem Pfad kombiniert.

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

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
