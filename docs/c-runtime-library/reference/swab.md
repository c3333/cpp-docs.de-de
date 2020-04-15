---
title: _swab
ms.date: 4/2/2020
api_name:
- _swab
- stdlib/_swab
- _o__swab
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _swab
- stdlib/_swab
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
ms.openlocfilehash: f7fe23cd9c1b2eab52ebe50904d0bb18fe16cea6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362952"
---
# <a name="_swab"></a>_swab

Tauscht Bytes.

## <a name="syntax"></a>Syntax

```C
void _swab(
   char *src,
   char *dest,
   int n
);
```

## <a name="parameters"></a>Parameter

*src*<br/>
Zu kopierende und tauschende Daten.

*dest*<br/>
Speicherort für getauschte Daten.

*n*<br/>
Anzahl der zu kopierenden und tauschender Bytes.

## <a name="return-value"></a>Rückgabewert

Die **Tupferfunktion** gibt keinen Wert zurück. Die Funktion setzt **errno** auf **EINVAL,** wenn entweder der *src-* oder *dest-Zeiger* null oder *n* kleiner als Null ist und der ungültige Parameterhandler aufgerufen wird, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Wenn *n* gerade ist, kopiert die **_swab-Funktion** *n* Bytes aus *src*, tauscht jedes Paar benachbarter Bytes aus und speichert das Ergebnis bei *dest*. Wenn *n* ungerade ist, **kopiert und** tauscht _swab die ersten *n*-1 Bytes von *src*aus, und das endgültige Byte wird nicht kopiert. Die **_swab** Funktion wird in der Regel verwendet, um binäre Daten für die Übertragung an einen Computer vorzubereiten, der eine andere Bytereihenfolge verwendet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_swab**|C: \<stdlib.h> C++: \<cstdlib> oder \<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_swab.c

#include <stdlib.h>
#include <stdio.h>

char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";
char to[] =   "...........................";

int main()
{
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);
    _swab(from, to, sizeof(from));
    printf("After:  %s\n        %s\n\n", from, to);
}
```

```Output
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes
        ...........................

After:  BADCFEHGJILKNMPORQTSVUXWZY
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.
```

## <a name="see-also"></a>Siehe auch

[Pufferbearbeitung](../../c-runtime-library/buffer-manipulation.md)<br/>
