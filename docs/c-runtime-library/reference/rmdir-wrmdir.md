---
title: _rmdir, _wrmdir
ms.date: 4/2/2020
api_name:
- _wrmdir
- _rmdir
- _o__rmdir
- _o__wrmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: dc9406371da950eb76207d8ddb4a1be8c732098e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338073"
---
# <a name="_rmdir-_wrmdir"></a>_rmdir, _wrmdir

Löscht ein Verzeichnis.

## <a name="syntax"></a>Syntax

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parameter

*Dirname*<br/>
Der Pfad des Verzeichnisses, das entfernt werden soll.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt 0 zurück, wenn das Verzeichnis erfolgreich gelöscht wird. Ein Rückgabewert von -1 gibt einen Fehler an und **errno** wird auf einen der folgenden Werte gesetzt:

|errno-Wert|Bedingung|
|-|-|
| **ENOTEMPTY** | Die angegebene Pfad ist kein Verzeichnis, das Verzeichnis ist nicht leer oder das Verzeichnis ist das aktuelle Arbeitsverzeichnis oder das Stammverzeichnis. |
| **ENOENT** | Der Pfad ist ungültig. |
| **EACCES** | Ein Programm verfügt über ein geöffnetes Handle des Verzeichnisses. |

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_rmdir-Funktion** löscht das von *dirname*angegebene Verzeichnis . Das Verzeichnis muss leer sein, und es darf sich nicht um das aktuelle Arbeitsverzeichnis oder das Stammverzeichnis handeln.

**_wrmdir** ist eine breit **gefächerte**Version von _rmdir ; Das *dirname-Argument* für **_wrmdir** ist eine Zeichenfolge mit großen Zeichen. **_wrmdir** und **_rmdir** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

Siehe Beispiele für [_mkdir](mkdir-wmkdir.md).

## <a name="see-also"></a>Siehe auch

[Verzeichnissteuerung](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
