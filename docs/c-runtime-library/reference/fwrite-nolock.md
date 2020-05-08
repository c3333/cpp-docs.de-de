---
title: _fwrite_nolock
ms.date: 4/2/2020
api_name:
- _fwrite_nolock
- _o__fwrite_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fwrite_nolock
- fwrite_nolock
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
ms.openlocfilehash: 6856dd2af0536deacfbef6b02c7cdf38d41f9c04
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919433"
---
# <a name="_fwrite_nolock"></a>_fwrite_nolock

Schreibt ein Zeichen in einen Stream, ohne den Thread zu sperren.

## <a name="syntax"></a>Syntax

```C
size_t _fwrite_nolock(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Zeiger auf die zu schreibenden Daten.

*size*<br/>
Elementgröße in Bytes.

*count*<br/>
Maximale Anzahl zu schreibender Elemente.

*Streich*<br/>
Zeiger zur **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Identisch mit [fwrite](fwrite.md).

## <a name="remarks"></a>Hinweise

Diese Funktion ist eine nicht sperrende Version von " **f**". Sie ist mit **fwrite** identisch, mit der Ausnahme, dass Sie nicht vor Störungen durch andere Threads geschützt ist. Sie ist möglicherweise schneller, da sie nicht den Mehraufwand zum Sperren anderer Threads mit sich bringt. Verwenden Sie diese Funktion nur in threadsicheren Kontexten wie z. B. in Singlethreadanwendungen oder in Fällen, in denen bereits der aufrufende Bereich die Threadisolation handhabt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [fread](fread.md).

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
