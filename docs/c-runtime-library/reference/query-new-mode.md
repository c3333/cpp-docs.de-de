---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 26fabc71337f1554b63909697b601a0bd9e86638
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216829"
---
# <a name="_query_new_mode"></a>_query_new_mode

Gibt eine ganze Zahl zurück, die den neuen handlermodus angibt, der **_set_new_mode** für **malloc**festgelegt wurde

## <a name="syntax"></a>Syntax

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Rückgabewert

Gibt den aktuellen neuen handlermodus für **malloc**zurück, nämlich 0 oder 1. Der Rückgabewert 1 gibt an, dass **malloc** bei einem Fehler beim Zuordnen von Arbeitsspeicher die neue Handlerroutine aufruft. der Rückgabewert 0 gibt an, dass dies nicht der Fall ist.

## <a name="remarks"></a>Bemerkungen

Die C++ **_query_new_mode** -Funktion gibt eine ganze Zahl zurück, die den neuen handlermodus angibt, der von der C++ [_set_new_mode](set-new-mode.md) -Funktion für [malloc](malloc.md)festgelegt wird. Der neue handlermodus gibt an, ob bei einem Fehler beim Zuweisen von Arbeitsspeicher **malloc** die neue Handlerroutine aufrufen soll, wie von [_set_new_handler](set-new-handler.md)festgelegt. Standardmäßig ruft **malloc** die neue Handlerroutine bei einem Fehler nicht auf. Sie können **_set_new_mode** verwenden, um dieses Verhalten zu überschreiben, sodass bei einem Fehler **malloc** die neue Handlerroutine auf die gleiche Weise aufgerufen wird, die der **`new`** Operator beim Zuordnen von Arbeitsspeicher vornimmt. Weitere Informationen finden Sie unter der Erläuterung [new and delete operators (Operatoren new und delete)](../../cpp/new-and-delete-operators.md) in der C++-Sprachreferenz.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Kosten](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
