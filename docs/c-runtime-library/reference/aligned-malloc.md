---
title: _aligned_malloc
ms.date: 4/2/2020
api_name:
- _aligned_malloc
- _o__aligned_malloc
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
- _aligned_malloc
- alligned_malloc
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
ms.openlocfilehash: 3caf2e8a3160c5533dfdb5bb387b373daf16b6e7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912924"
---
# <a name="_aligned_malloc"></a>_aligned_malloc

Weist Speicher mit einer definierten Zuweisungsgrenze zu.

## <a name="syntax"></a>Syntax

```C
void * _aligned_malloc(
    size_t size,
    size_t alignment
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Die Größe der angeforderten Speicherbelegung.

*Richt*<br/>
Der Ausrichtungswert, der eine ganzzahlige Potenz von 2 sein muss.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der zugeordnet wurde, oder NULL, wenn der Vorgang fehlgeschlagen ist. Der Zeiger ist ein Vielfaches der *Ausrichtung*.

## <a name="remarks"></a>Hinweise

**_aligned_malloc** basiert auf [malloc](malloc.md).

**_aligned_malloc** ist als `__declspec(noalias)` und `__declspec(restrict)`gekennzeichnet, was bedeutet, dass die Funktion globale Variablen garantiert nicht ändert und dass der zurückgegebene Zeiger keinen Alias hat. Weitere Informationen finden Sie unter [noalias](../../cpp/noalias.md) und [restrict](../../cpp/restrict.md).

Diese Funktion legt `errno` auf `ENOMEM` fest, wenn die Speicherbelegung fehlgeschlagen ist oder die angeforderte Größe größer als `_HEAP_MAXREQ` war. Weitere Informationen zu `errno` finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Außerdem überprüft **_aligned_malloc** seine Parameter. Wenn die *Ausrichtung* keine Potenz von 2 ist oder die *Größe* 0 (null) ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion NULL zurück und `errno` legt `EINVAL`auf fest.

Verwenden Sie [_aligned_free](aligned-free.md) , um den von **_aligned_malloc** und `_aligned_offset_malloc`ermittelbaren Speicherplatz zu verringern. Verwenden `free`Sie nicht, wodurch der ausgerichtete Arbeitsspeicher nicht ordnungsgemäß freigegeben wird und Fehler bei der Fehlerdiagnose auftreten können.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_aligned_malloc**|\<malloc.h>|

## <a name="example"></a>Beispiel

```C
// crt_aligned_malloc.c

#include <malloc.h>
#include <stdio.h>

int main() {
    void    *ptr;
    size_t  alignment,
            off_set;

    // Note alignment should be 2^N where N is any positive int.
    alignment = 16;
    off_set = 5;

    // Using _aligned_malloc
    ptr = _aligned_malloc(100, alignment);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned memory.");
        return -1;
    }
    if (((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);

    // Using _aligned_realloc
    ptr = _aligned_realloc(ptr, 200, alignment);
    if ( ((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);
    _aligned_free(ptr);

    // Using _aligned_offset_malloc
    ptr = _aligned_offset_malloc(200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu "
                  "and alignment %zu\n",ptr, off_set, alignment);

    // Using _aligned_offset_realloc
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error reallocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu and "
                  "alignment %zu\n", ptr, off_set, alignment);

    // Note that _aligned_free works for both _aligned_malloc
    // and _aligned_offset_malloc. Using free is illegal.
    _aligned_free(ptr);
}
```

```Output
This pointer, 3280880, is aligned on 16
This pointer, 3280880, is aligned on 16
This pointer, 3280891, is offset by 5 on alignment of 16
This pointer, 3280891, is offset by 5 on alignment of 16
```

## <a name="see-also"></a>Weitere Informationen

[Daten Ausrichtung](../../c-runtime-library/data-alignment.md)
