---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: c719f62a089b1c233bac193f3431d0375af826eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910258"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

Ändert die Größe eines Speicherblocks, der mit [_aligned_malloc](aligned-malloc.md) oder [_aligned_offset_malloc](aligned-offset-malloc.md) belegt wurde.

## <a name="syntax"></a>Syntax

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parameter

*memblock*<br/>
Der Zeiger auf den aktuellen Speicherblock.

*size*<br/>
Die Größe der Speicherbelegung.

*Richt*<br/>
Der Ausrichtungswert, der eine ganzzahlige Potenz von 2 sein muss.

*offset*<br/>
Der Offset in der Speicherbelegung zum Erzwingen der Ausrichtung.

## <a name="return-value"></a>Rückgabewert

**_aligned_offset_realloc** gibt einen void-Zeiger auf den neu belegten (und möglicherweise verschobenden) Speicherblock zurück. Der Rückgabewert ist **null** , wenn die Größe 0 (null) ist und das Puffer Argument nicht **null**ist, oder wenn nicht genügend Arbeitsspeicher verfügbar ist, um den Block auf die angegebene Größe zu erweitern. Im ersten Fall wird der ursprüngliche Block freigegeben. Im zweiten Fall wird der ursprüngliche Block nicht geändert. Der Rückgabewert zeigt auf einen Speicherplatz, der für die Speicherung eines beliebigen Objekttyps geeignet ist. Um einen Zeiger auf einen anderen Typ als den leeren zurückzugeben, verwenden Sie eine Typumwandlung für den Rückgabewert.

**_aligned_offset_realloc** ist als `__declspec(noalias)` und `__declspec(restrict)`gekennzeichnet, was bedeutet, dass die Funktion globale Variablen garantiert nicht ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Hinweise

Wie [_aligned_offset_malloc](aligned-offset-malloc.md)ermöglicht **_aligned_offset_realloc** , dass eine Struktur an einem Offset innerhalb der Struktur ausgerichtet wird.

**_aligned_offset_realloc** basiert auf **malloc**. Weitere Informationen zum Verwenden von **_aligned_offset_malloc**finden Sie unter [malloc](malloc.md). Wenn *memblock* **null**ist, ruft die Funktion intern **_aligned_offset_malloc** auf.

Diese Funktion legt **errno** auf **ENOMEM** fest, wenn die Speicher Belegung fehlgeschlagen ist oder die angeforderte Größe größer als **_HEAP_MAXREQ**ist. Weitere Informationen zu **errno**finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Außerdem überprüft **_aligned_offset_realloc** seine Parameter. Wenn die *Ausrichtung* keine Potenz von 2 ist oder *Offset* größer oder gleich *Größe* und ungleich NULL ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion **null** zurück und legt **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Weitere Informationen

[Daten Ausrichtung](../../c-runtime-library/data-alignment.md)<br/>
