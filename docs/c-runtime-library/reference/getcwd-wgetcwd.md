---
title: _getcwd, _wgetcwd
description: C-Lauf Zeit Bibliotheksfunktionen _getcwd, _wgetcwd das aktuelle Arbeitsverzeichnis erhalten.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 950f4f73912d7bab38363e41c61025d27380bef6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915749"
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

*ert*\
Speicherort für den Pfad.

*maxlen*\
Maximale Länge des Pfads in Zeichen: **char** für **_getcwd** und **wchar_t** für **_wgetcwd**.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den *Puffer*zurück. Ein **null** -Rückgabewert gibt einen Fehler an, und **errno** wird entweder auf **ENOMEM**festgelegt, was darauf hinweist, dass nicht genügend Arbeitsspeicher vorhanden ist, um *maxlen* -Bytes zuzuordnen (wenn ein **null** -Argument als *Puffer*angegeben wird), oder auf **ERANGE**, um anzugeben, dass der Pfad länger als *maxlen* -Zeichen ist. Wenn *maxlen* kleiner oder gleich 0 (null) ist, ruft diese Funktion einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_getcwd** -Funktion Ruft den vollständigen Pfad des aktuellen Arbeitsverzeichnisses für das Standard Laufwerk ab und speichert Sie im *Puffer*. Das ganzzahlige Argument *maxlen* gibt die maximale Länge für den Pfad an. Ein Fehler tritt auf, wenn die Länge des Pfads (einschließlich des abschließenden NULL-Zeichens) *maxlen*überschreitet. Das *buffer* -Argument kann **null**sein. ein Puffer mit einer minimalen Größe von *maxlen* (nur bei Bedarf) wird automatisch mit **malloc**zugeordnet, um den Pfad zu speichern. Dieser Puffer kann später freigegeben werden, indem Sie " **Free** " aufrufen und ihm den **_getcwd** Rückgabewert (einen Zeiger auf den zugeordneten Puffer) übergeben.

**_getcwd** gibt eine Zeichenfolge zurück, die den Pfad des aktuellen Arbeitsverzeichnisses darstellt. Wenn das aktuelle Arbeitsverzeichnis das Stammverzeichnis ist, endet die Zeichenfolge mit einem umgekehrten`\`Schrägstrich (). Wenn das aktuelle Arbeitsverzeichnis nicht das Stammverzeichnis ist, endet die Zeichenfolge mit dem Verzeichnisnamen und nicht mit einem umgekehrten Schrägstrich.

**_wgetcwd** ist eine breit Zeichen Version von **_getcwd**. Das *Puffer* Argument und der Rückgabewert von **_wgetcwd** sind Zeichen folgen mit breit Zeichen. **_wgetcwd** und **_getcwd** Verhalten sich andernfalls identisch.

Wenn **_DEBUG** und **_CRTDBG_MAP_ALLOC** definiert sind, werden Aufrufe von **_getcwd** und **_wgetcwd** durch Aufrufe von **_getcwd_dbg** und **_wgetcwd_dbg** ersetzt, um das Debuggen von Speicher Belegungen zu ermöglichen. Weitere Informationen finden Sie unter [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Verzeichnis Steuerung](../../c-runtime-library/directory-control.md)\
[_chdir _wchdir](chdir-wchdir.md)\
[_mkdir _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
