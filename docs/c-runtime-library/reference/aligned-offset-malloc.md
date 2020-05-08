---
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 0a0dca94ec03286c92b3cbf1a51df59a1ca7af0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919492"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

Weist Speicher mit einer definierten Zuweisungsgrenze zu.

## <a name="syntax"></a>Syntax

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die Größe der angeforderten Speicherbelegung.

*Richt*<br/>
Der Ausrichtungswert, der eine ganzzahlige Potenz von 2 sein muss.

*offset*<br/>
Der Offset in der Speicherbelegung zum Erzwingen der Ausrichtung.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der zugeordnet wurde, oder **null** , wenn der Vorgang fehlgeschlagen ist.

## <a name="remarks"></a>Hinweise

**_aligned_offset_malloc** ist in Situationen nützlich, in denen eine Ausrichtung für ein unter strukturetes Element erforderlich ist. beispielsweise, wenn die Ausrichtung für eine in einer Klasse eine Klasse erforderlich war.

**_aligned_offset_malloc** basiert auf **malloc**. Weitere Informationen finden Sie unter [malloc](malloc.md).

**_aligned_offset_malloc** ist als `__declspec(noalias)` und `__declspec(restrict)`gekennzeichnet, was bedeutet, dass die Funktion globale Variablen garantiert nicht ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Diese Funktion legt **errno** auf **ENOMEM** fest, wenn die Speicher Belegung fehlgeschlagen ist oder die angeforderte Größe größer als **_HEAP_MAXREQ**ist. Weitere Informationen zu **errno**finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Außerdem überprüft **_aligned_offset_malloc** seine Parameter. Wenn die *Ausrichtung* keine Potenz von 2 ist oder *Offset* größer oder gleich *Größe* und ungleich NULL ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion **null** zurück und legt **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Weitere Informationen

[Daten Ausrichtung](../../c-runtime-library/data-alignment.md)<br/>
