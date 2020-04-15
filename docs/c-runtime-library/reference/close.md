---
title: _close
ms.date: 4/2/2020
api_name:
- _close
- _o__close
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: 4d8b702a10624ae80629b4ce4644c428322500cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348646"
---
# <a name="_close"></a>_close

Schließt eine Datei.

## <a name="syntax"></a>Syntax

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor, der auf die geöffnete Datei verweist.

## <a name="return-value"></a>Rückgabewert

**_close** gibt 0 zurück, wenn die Datei erfolgreich geschlossen wurde. Ein Rückgabewert von -1 gibt einen Fehler an.

## <a name="remarks"></a>Bemerkungen

Die **_close-Funktion** schließt die Datei, die *fd*zugeordnet ist.

Der Dateideskriptor und das zugrunde liegende Betriebssystem-Dateihandle werden geschlossen. Daher ist es nicht notwendig, **CloseHandle** aufzurufen, wenn die Datei ursprünglich mit der Win32-Funktion **CreateFile** geöffnet und mit **_open_osfhandle**in einen Dateideskriptor konvertiert wurde.

Diese Funktion überprüft ihre Parameter. Wenn *fd* ein fehlerhafter Dateideskriptor ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben die Funktionen -1 zurück und **errno** wird auf **EBADF**gesetzt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_open](open-wopen.md).

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
