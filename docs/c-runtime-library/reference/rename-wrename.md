---
title: rename, _wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- _wrename
- _trename
- Rename
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338108"
---
# <a name="rename-_wrename"></a>rename, _wrename

Benennt eine Datei oder ein Verzeichnis um.

## <a name="syntax"></a>Syntax

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>Parameter

*oldname*<br/>
Zeiger auf den alten Namen.

*newname*<br/>
Zeiger auf den neuen Namen.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt bei Erfolg 0 zurück. Bei einem Fehler gibt die Funktion einen Wert ungleich Null zurück und legt **errno** auf einen der folgenden Werte fest:

|errno-Wert|Bedingung|
|-|-|
| **EACCES** | Die Datei oder das Verzeichnis, das von *newname* angegeben wird, ist bereits vorhanden oder konnte nicht erstellt werden (ungültiger Pfad). Möglicherweise ist auch *oldname* ein Verzeichnis, und *newname* gibt einen anderen Pfad an. |
| **ENOENT** | Von *oldname* angegebene Datei oder Pfad wurden nicht gefunden. |
| **Einval** | Name enthält ungültige Zeichen. |

Weitere mögliche Rückgabewerte finden Sie unter [_doserrno, _errno, syserrlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **rename**-Funktion benennt die Datei oder das Verzeichnis, die von *oldname* angegeben wurden, auf den von *newname* gegebenen Namen. Der alte Name muss der Pfad einer vorhandenen Datei oder eines vorhandenen Verzeichnisses sein. Der neue Name darf nicht der Name einer vorhandenen Datei oder eines vorhandenen Verzeichnisses sein. Sie können **rename** nutzen, um eine Datei von einem Verzeichnis oder Gerät zu einem anderen zu verschieben, indem Sie einen anderen Pfad im *newname*-Argument angeben. Allerdings können Sie **rename** nicht verwenden, um ein Verzeichnis zu verschieben. Verzeichnisse können umbenannt, aber nicht verschoben werden.

**_wrename** ist eine breit gefächerte Version von **_rename**; Die Argumente für **_wrename** sind Zeichenfolgen mit großen Zeichen. **_wrename** und **_rename** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**rename**|**rename**|**_wrename**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**rename**|\<io.h> oder \<stdio.h>|
|**_wrename**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>Output

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
