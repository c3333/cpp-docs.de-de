---
title: _commit
ms.date: 4/2/2020
api_name:
- _commit
- _o__commit
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
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: f8e13e7fc197c66395556d518ecbd1cd20ac1f77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348615"
---
# <a name="_commit"></a>_commit

Leert eine Datei direkt auf den Datenträger.

## <a name="syntax"></a>Syntax

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor, der auf die geöffnete Datei verweist.

## <a name="return-value"></a>Rückgabewert

**_commit** gibt 0 zurück, wenn die Datei erfolgreich auf den Datenträger geleert wurde. Ein Rückgabewert von -1 gibt einen Fehler an.

## <a name="remarks"></a>Bemerkungen

Die **_commit-Funktion** zwingt das Betriebssystem, die datei, die *fd* zugeordnet ist, auf den Datenträger zu schreiben. Dieser Aufruf stellt sicher, dass die angegebene Datei sofort geleert wird (und nicht nach Ermessen des Betriebssystems).

Wenn *fd* ein ungültiger Dateideskriptor ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion -1 zurück und **errno** wird auf **EBADF**gesetzt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
