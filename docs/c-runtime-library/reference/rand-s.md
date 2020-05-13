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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: cad1740e64c7bbda553ac1a6c777d7e2295152ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919541"
---
# <a name="rand_s"></a>rand_s

Generiert eine pseudozufällige Zahl. Dies ist eine sicherere Version der Funktion [Rand](rand.md), mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md)beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parameter

*randomValue*<br/>
Ein Zeiger auf eine Ganzzahl, die den generierten Wert enthalten soll.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode. Wenn der Eingabe Zeiger _randomValue_ ein NULL-Zeiger ist, ruft die Funktion einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion **EINVAL** zurück und legt **errno** auf **EINVAL**fest. Wenn die Funktion aus einem anderen Grund fehlschlägt, wird "*_randomValue_ " auf "0" festgelegt.

## <a name="remarks"></a>Hinweise

Die **rand_s** -Funktion schreibt eine Pseudo Zufalls-Ganzzahl im Bereich 0, um an den Eingabe Zeiger zu **UINT_MAX** . Die **rand_s** Funktion verwendet das Betriebssystem, um kryptografisch sichere Zufallszahlen zu generieren. Er verwendet nicht den von der [srand](srand.md) -Funktion generierten Ausgangswert und wirkt sich nicht auf die Zufallszahlen Sequenz aus, die von [Rand](rand.md)verwendet wird.

Die **rand_s** -Funktion erfordert, dass Konstante **_CRT_RAND_S** vor der Inklusions Anweisung definiert werden, damit die Funktion deklariert wird, wie im folgenden Beispiel gezeigt:

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** hängt von der [rtlgenrandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) -API ab, die nur unter Windows XP und höher verfügbar ist.

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

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
