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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 7d5f62bd6111a305c18b0ee19bb6d3e90f2ddb49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338666"
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

**_msize** gibt die Größe (in Bytes) als ganzzahlige Datei ohne Vorzeichen zurück.

## <a name="remarks"></a>Bemerkungen

Die **_msize-Funktion** gibt die Größe des Speicherblocks in Bytes zurück, der durch einen Aufruf von **calloc**, **malloc**oder **realloc**zugewiesen wurde.

Wenn die Anwendung mit einer Debugversion der C-Laufzeitbibliotheken verknüpft ist, **wird _msize** [in _msize_dbg](msize-dbg.md)aufgelöst. Weitere Informationen dazu, wie der Heap während des Debugprozesses verwaltet wird, finden Sie unter [The CRT Debug Heap (CRT-Debugheap)](/visualstudio/debugger/crt-debug-heap-details).

Diese Funktion überprüft seine Parameter. Wenn *memblock* ein Nullzeiger ist, **ruft _msize** einen ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn der Fehler behandelt wird, setzt die Funktion **errno** auf **EINVAL** und gibt -1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

Ein Beispiel finden Sie unter [realloc](realloc.md).

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
