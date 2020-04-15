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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 46d07a8b3645ae0d68276d96271be0a246716f0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361218"
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

## <a name="remarks"></a>Bemerkungen

Die **_unlock_file-Funktion** entsperrt die durch *Datei*angegebene Datei . Das Entsperren einer Datei ermöglicht anderen Prozessen den Zugriff auf die Datei. Diese Funktion sollte nur aufgerufen **werden,** wenn zuvor _lock_file für den *Dateizeiger* aufgerufen wurde. Das Aufrufen **_unlock_file** einer Datei, die nicht gesperrt ist, kann zu einem Deadlock führen. Ein Beispiel finden Sie unter [_lock_file](lock-file.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_unlock_file**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_lock_file](lock-file.md)<br/>
