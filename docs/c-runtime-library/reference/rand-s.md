---
title: rand_s
ms.date: 4/2/2020
api_name:
- rand_s
- _o_rand_s
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
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: b11a40dd9dc58964df77330767a55aa95a179319
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338203"
---
# <a name="rand_s"></a>rand_s

Generiert eine pseudozufällige Zahl. Dies ist eine sicherere Version der Funktion [rand](rand.md), mit Sicherheitsverbesserungen, wie unter [Sicherheitsfeatures in der CRT](../../c-runtime-library/security-features-in-the-crt.md)beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parameter

*randomValue*<br/>
Ein Zeiger auf eine ganze Zahl, die den generierten Wert aufhält.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode. Wenn der Eingabezeiger _randomValue_ ein NULL-Zeiger ist, ruft die Funktion einen ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion **EINVAL** zurück und setzt **errno** auf **EINVAL**. Wenn die Funktion aus einem anderen Grund fehlschlägt, wird *_randomValue_ auf 0 gesetzt.

## <a name="remarks"></a>Bemerkungen

Die **rand_s-Funktion** schreibt eine Pseudorandom-Ganzzahl im Bereich 0 bis **UINT_MAX** in den Eingabezeiger. Die **rand_s-Funktion** verwendet das Betriebssystem, um kryptographisch sichere Zufallszahlen zu generieren. Es verwendet nicht den Samen, der von der [Srand-Funktion](srand.md) erzeugt wird, noch beeinflusst es die zufällige Zahlenfolge, die von [rand](rand.md)verwendet wird.

Die **funktion rand_s** erfordert, dass konstante **_CRT_RAND_S** vor der Inclusion-Anweisung für die zu deklarierende Funktion definiert werden, wie im folgenden Beispiel:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** hängt von der [RtlGenRandom-API](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) ab, die nur in Windows XP und höher verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
