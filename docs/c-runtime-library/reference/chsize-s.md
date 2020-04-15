---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350076"
---
# <a name="_chsize_s"></a>_chsize_s

Ändert die Größe einer Datei. Dies ist eine sicherere Version von [_chsize](chsize.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor, der auf eine geöffnete Datei verweist.

*Größe*<br/>
Neue Länge der Datei in Bytes.

## <a name="return-value"></a>Rückgabewert

**_chsize_s** gibt den Wert 0 zurück, wenn die Dateigröße erfolgreich geändert wurde. Ein Rückgabewert ungleich Null gibt einen Fehler an: Der Rückgabewert ist **EACCES,** wenn die angegebene Datei für den Zugriff gesperrt ist, **EBADF,** wenn die angegebene Datei schreibgeschützt ist oder der Deskriptor ungültig ist, **ENOSPC,** wenn kein Speicherplatz auf dem Gerät verbleibt, oder **EINVAL,** wenn die Größe kleiner als Null ist. **errno** wird auf denselben Wert gesetzt.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_chsize_s-Funktion** erweitert oder abgeschnitten die Datei, die fd zugeordnet *ist,* auf die durch *Größe*angegebene Länge. Die Datei muss in einem Modus geöffnet sein, der Schreiben zulässt. Wenn die Datei erweitert wird, werden NULL-Zeichen ('\0') angefügt. Wenn die Datei abgeschnitten wird, gehen alle Daten vom Ende der gekürzten Datei bis zur ursprünglichen Länge der Datei verloren.

**_chsize_s** nimmt eine 64-Bit-Ganzzahl als Dateigröße und kann daher Dateigrößen größer als 4 GB verarbeiten. **_chsize** ist auf 32-Bit-Dateigrößen beschränkt.

Diese Funktion überprüft ihre Parameter. Wenn *fd* kein gültiger Dateideskriptor ist oder die Größe kleiner als Null ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
