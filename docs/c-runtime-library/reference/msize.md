---
title: _msize
ms.date: 4/2/2020
api_name:
- _msize
- _o__msize
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: cc8eef0d28f649340715edbf4b1ebdfea85c2ff2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914612"
---
# <a name="_msize"></a>_msize

Gibt die Größe eines im Heap belegten Speicherblocks zurück.

## <a name="syntax"></a>Syntax

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parameter

*memblock*<br/>
Zeiger zum Speicherblock.

## <a name="return-value"></a>Rückgabewert

**_msize** gibt die Größe (in Bytes) als ganze Zahl ohne Vorzeichen zurück.

## <a name="remarks"></a>Hinweise

Die **_msize** -Funktion gibt die Größe des Speicherblocks (in Bytes) zurück, der durch einen **czuzuordnungs**-, **malloc**-oder **rezuordnungsbefehl**zugeordnet wird.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, wird **_msize** in [_msize_dbg](msize-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

Diese Funktion überprüft seine Parameter. Wenn *memblock* ein NULL-Zeiger ist, ruft **_msize** einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn der Fehler behandelt wird, legt die Funktion **errno** auf **EINVAL** fest und gibt-1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

Ein Beispiel finden Sie unter [realloc](realloc.md).

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
