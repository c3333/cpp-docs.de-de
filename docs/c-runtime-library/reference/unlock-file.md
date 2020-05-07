---
title: _unlock_file
ms.date: 4/2/2020
api_name:
- _unlock_file
- _o__unlock_file
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
- _unlock_file
- unlock_file
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
ms.openlocfilehash: ed79f66baebf71c89e537c8343779bef44ebfbb8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909206"
---
# <a name="_unlock_file"></a>_unlock_file

Hebt die Sperre einer Datei auf, sodass andere Prozesse auf die Datei zugreifen können.

## <a name="syntax"></a>Syntax

```C
void _unlock_file(
   FILE* file
);
```

### <a name="parameters"></a>Parameter

*Datei*<br/>
Dateihandle.

## <a name="remarks"></a>Hinweise

Die **_unlock_file** -Funktion entsperrt die Datei, die in der *Datei*angegeben ist. Das Entsperren einer Datei ermöglicht anderen Prozessen den Zugriff auf die Datei. Diese Funktion sollte nur aufgerufen werden, wenn **_lock_file** zuvor für den *Datei* Zeiger aufgerufen wurde. Das Aufrufen von **_unlock_file** in einer Datei, die nicht gesperrt ist, kann zu einem Deadlock führen. Ein Beispiel finden Sie unter [_lock_file](lock-file.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
