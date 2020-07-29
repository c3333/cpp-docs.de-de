---
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 9c87a63a9ed94eb1473230aedb5e9c17fcc6410b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216842"
---
# <a name="_query_new_handler"></a>_query_new_handler

Gibt die Adresse der aktuellen neuen Handlerroutine zurück.

## <a name="syntax"></a>Syntax

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Rückgabewert

Gibt die Adresse der aktuellen neuen Handlerroutine zurück, die durch **_set_new_handler**festgelegt ist.

## <a name="remarks"></a>Bemerkungen

Die C++ **_query_new_handler** -Funktion gibt die Adresse der aktuellen Ausnahme Behandlungs Funktion zurück, die von der C++ [_set_new_handler](set-new-handler.md) -Funktion festgelegt wird. **_set_new_handler** wird verwendet, um eine Ausnahme Behandlungs Funktion anzugeben, die gesteuert werden soll, wenn der **`new`** Operator keinen Arbeitsspeicher zuordnen kann. Weitere Informationen finden Sie unter der Erläuterung [new and delete operators (Operatoren new und delete)](../../cpp/new-and-delete-operators.md) in der C++-Sprachreferenz.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[Kosten](free.md)<br/>
