---
title: _heapadd
ms.date: 11/04/2016
api_name:
- _heapadd
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: c5eeb66ff0e6fb05063ec395e12cd97106ad724d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351321"
---
# <a name="_heapadd"></a>_heapadd

Fügt dem Heap Arbeitsspeicher hinzu.

> [!IMPORTANT]
> Diese Funktion ist veraltet. Von Visual Studio 2015 an ist sie nicht in der CRT verfügbar.

## <a name="syntax"></a>Syntax

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parameter

*memblock*<br/>
Zeiger auf den Heapspeicher.

*Größe*<br/>
Größe des hinzuzufügenden Speichers in Byte.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt `_heapadd` „0“ (null) zurück; andernfalls gibt die Funktion „-1“ zurück und legt `errno` auf `ENOSYS` fest.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist, and _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Von Visual C++, Version 4.0, an, wurde die zugrundeliegende Heapstruktur in die C-Laufzeitbibliotheken verschoben, um die neuen Debugfunktionen zu unterstützen. Das hat zur Folge, dass `_heapadd` auf Plattformen, die auf der Win32-API basieren, nicht mehr unterstützt wird.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../c-runtime-library/compatibility.md) in der Einführung.

## <a name="see-also"></a>Siehe auch

[Speicherzuweisung](../c-runtime-library/memory-allocation.md)<br/>
[kostenlos](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
