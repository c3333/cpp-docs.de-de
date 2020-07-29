---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: a31617445ccb0640042be41ee4f710e528b9ceb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229453"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Debugversionen der Funktionen [_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md) (nur während des Debuggens verfügbar).

## <a name="syntax"></a>Syntax

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parameter

*Antrie*<br/>
Name des Laufwerks.

*ert*<br/>
Speicherort für den Pfad.

*maxlen*<br/>
Maximale Länge des Pfads in Zeichen: **`char`** für **_getdcwd_dbg** und **`wchar_t`** für **_wgetdcwd_dbg**.

*blockType*<br/>
Angeforderter Typ des Speicherblocks: **_CLIENT_BLOCK** oder **_NORMAL_BLOCK**.

*filename*<br/>
Zeiger auf den Namen der Quelldatei, die den Zuordnungs Vorgang angefordert hat, oder **null**.

*LineNumber*<br/>
Zeilennummer in der Quelldatei, in der der Zuordnungs Vorgang angefordert wurde, oder **null**.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den *Puffer*zurück. Ein **null** -Rückgabewert gibt einen Fehler an, und **errno** wird entweder auf **ENOMEM**festgelegt, was darauf hinweist, dass nicht genügend Arbeitsspeicher vorhanden ist, um *maxlen* -Bytes zuzuordnen (wenn ein **null** -Argument als *Puffer*angegeben wird), oder auf **ERANGE**, um anzugeben, dass der Pfad länger als *maxlen* -Zeichen ist. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die Funktionen **_getdcwd_dbg** und **_wgetdcwd_dbg** sind identisch mit **_getdcwd** und **_wgetdcwd** , mit dem Unterschied, dass, wenn **_DEBUG** definiert ist, diese Funktionen die Debugversion von **malloc** und **_malloc_dbg** verwenden, um Speicher zuzuweisen, wenn **null** als *Puffer* Parameter übergeben wird. Weitere Informationen finden Sie unter [_malloc_dbg](malloc-dbg.md).

In den meisten Fällen müssen Sie diese Funktionen nicht explizit aufrufen. Stattdessen können Sie das **_CRTDBG_MAP_ALLOC** -Flag definieren. Wenn **_CRTDBG_MAP_ALLOC** definiert ist, werden Aufrufe von **_getdcwd** und **_wgetdcwd** **_getdcwd_dbg** bzw. **_wgetdcwd_dbg**neu zugeordnet, wobei *blockType* auf **_NORMAL_BLOCK**festgelegt ist. Daher müssen Sie diese Funktionen nicht explizit aufzurufen, es sei denn, Sie möchten die Heap Blöcke als **_CLIENT_BLOCK**markieren. Weitere Informationen finden Sie unter [Blocktypen auf dem](/visualstudio/debugger/crt-debug-heap-details)Debugheap.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Verzeichnis Steuerung](../../c-runtime-library/directory-control.md)<br/>
[Debugversionen von Heapreservierungsfunktionen](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
