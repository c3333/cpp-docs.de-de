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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c642820bf1bc2e2afbd14e17832fb3fdb6f865b8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919855"
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

*FD*<br/>
Dateideskriptor, der auf die geöffnete Datei verweist.

## <a name="return-value"></a>Rückgabewert

**_close** gibt 0 zurück, wenn die Datei erfolgreich geschlossen wurde. Der Rückgabewert-1 gibt einen Fehler an.

## <a name="remarks"></a>Hinweise

Die **_close** -Funktion schließt die mit *FD*verknüpfte Datei.

Der Dateideskriptor und das zugrunde liegende Betriebssystem-Dateihandle werden geschlossen. Folglich ist es nicht notwendig, **CloseHandle** aufzurufen, wenn die Datei ursprünglich mit der **Win32-Funktion** "" in der Datei "" mit der Datei "" von " **_open_osfhandle**" in einen Dateideskriptor konvertiert wurde.

Diese Funktion überprüft ihre Parameter. Wenn *FD* ein fehlerhafter Dateideskriptor ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück, und **errno** ist auf **EBADF**festgelegt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_open](open-wopen.md).

## <a name="see-also"></a>Weitere Informationen

[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
