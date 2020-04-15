---
title: _getcwd, _wgetcwd
description: C Runtime Library-Funktionen _getcwd _wgetcwd das aktuelle Arbeitsverzeichnis abrufen.
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344435"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd, _wgetcwd

Ruft das aktuelle Arbeitsverzeichnis ab.

## <a name="syntax"></a>Syntax

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parameter

*Puffer*\
Speicherort für den Pfad.

*maxlen*\
Maximale Länge des Pfads in Zeichen: **zeichen** für **_getcwd** und **wchar_t** für **_wgetcwd**.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf *den Puffer*zurück. Ein **NULL-Rückgabewert** gibt einen Fehler an, und **errno** wird entweder auf **ENOMEM**festgelegt, was darauf hinweist, dass nicht genügend Arbeitsspeicher vorhanden ist, um *maxlen* Bytes zuzuweisen (wenn ein **NULL-Argument** als *Puffer*angegeben wird), oder auf **ERANGE**, was darauf hinweist, dass der Pfad länger als *maxlen-Zeichen* ist. Wenn *maxlen* kleiner oder gleich Null ist, ruft diese Funktion einen ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_getcwd-Funktion** ruft den vollständigen Pfad des aktuellen Arbeitsverzeichnisses für das Standardlaufwerk ab und speichert es im *Puffer*. Das Ganzzahlargument *maxlen* gibt die maximale Länge für den Pfad an. Ein Fehler tritt auf, wenn die Länge des Pfads (einschließlich des beendenden Nullzeichens) *maxlen*überschreitet. Das *Pufferargument* kann **NULL**sein. Ein Puffer von mindestens der Größe *maxlen* (mehr nur bei Bedarf) wird automatisch mit **malloc**zugewiesen, um den Pfad zu speichern. Dieser Puffer kann später freigegeben werden, indem der **_getcwd** Rückgabewert (ein Zeiger auf den zugewiesenen Puffer) **aufgerufen** und übergeben wird.

**_getcwd** gibt eine Zeichenfolge zurück, die den Pfad des aktuellen Arbeitsverzeichnisses darstellt. Wenn das aktuelle Arbeitsverzeichnis der Stamm ist, endet`\`die Zeichenfolge mit einem umgekehrten Schrägstrich ( ). Wenn das aktuelle Arbeitsverzeichnis nicht das Stammverzeichnis ist, endet die Zeichenfolge mit dem Verzeichnisnamen und nicht mit einem umgekehrten Schrägstrich.

**_wgetcwd** ist eine breit gefächerte Version von **_getcwd**; Das *Pufferargument* und der Rückgabewert von **_wgetcwd** sind Zeichenfolgen mit großen Zeichen. **_wgetcwd** und **_getcwd** verhalten sich ansonsten gleich.

Wenn **_DEBUG** und **_CRTDBG_MAP_ALLOC** definiert sind, werden Aufrufe von **_getcwd** und **_wgetcwd** durch Aufrufe **von _getcwd_dbg** und **_wgetcwd_dbg** ersetzt, um das Debuggen von Speicherzuweisungen zu ermöglichen. Weitere Informationen finden Sie unter [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Siehe auch

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
