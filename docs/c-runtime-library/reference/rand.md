---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 944c512d0102b459afc2924ef7515311e46cd43c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338163"
---
# <a name="rand"></a>rand

Generiert eine Pseudozufallszahl mithilfe eines bekannten und vollständig reproduzierbaren Algorithmus. Eine programmgesteuert sichere Version dieser Funktion ist verfügbar. siehe [rand_s](rand-s.md). Zahlen, die von **rand** generiert werden, sind nicht kryptographisch sicher. Für eine kryptographisch sichere Zufallszahlengenerierung verwenden Sie [rand_s](rand-s.md) oder die in der C++-Standardbibliothek deklarierten Funktionen in [ \<zufälligen>](../../standard-library/random.md).

## <a name="syntax"></a>Syntax

```C
int rand( void );
```

## <a name="return-value"></a>Rückgabewert

**rand** gibt eine Pseudozufallszahl zurück, wie oben beschrieben. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Die **rand-Funktion** gibt eine Pseudorandom-Ganzzahl im Bereich 0 bis **RAND_MAX** (32767) zurück. Verwenden Sie die [Srand-Funktion,](srand.md) um den Pseudorandom-Zahlengenerator auszusieren, bevor Sie **rand**aufrufen.

Die **rand-Funktion** erzeugt eine bekannte Sequenz und ist nicht für die Verwendung als kryptografische Funktion geeignet. Für eine kryptographisch sichere Zufallszahlengenerierung verwenden Sie [rand_s](rand-s.md) oder die in der C++-Standardbibliothek deklarierten Funktionen in [ \<zufälligen>](../../standard-library/random.md). Informationen darüber, was mit **rand** \<falsch ist und wie zufällig> diese Mängel behebt, finden Sie in diesem Video mit dem Titel [rand Considered Harmful](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
