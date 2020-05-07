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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8f2a4d00310671e8ba80055e38e479e348562ac2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919527"
---
# <a name="rand"></a>rand

Generiert eine Pseudo Zufalls-Zahl mithilfe eines bekannten und vollständig reproduzierbaren Algorithmus. Eine Programm gesteuert sichere Version dieser Funktion ist verfügbar. siehe [rand_s](rand-s.md). Die von **Rand** generierten Zahlen sind nicht kryptografisch sicher. Verwenden Sie zum Generieren einer kryptografisch sicheren Zufallszahlengenerierung [rand_s](rand-s.md) oder die in der C++-Standard Bibliothek in [ \<Random>](../../standard-library/random.md)deklarierten Funktionen.

## <a name="syntax"></a>Syntax

```C
int rand( void );
```

## <a name="return-value"></a>Rückgabewert

**Rand** gibt eine Pseudo Zufallszahl zurück, wie oben beschrieben. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Hinweise

Die **Rand** -Funktion gibt eine Pseudo Zufalls-Ganzzahl im Bereich 0 bis **RAND_MAX** (32767) zurück. Verwenden Sie die [srand](srand.md) -Funktion, um einen Ausgangswert für den Pseudozufallszahlen-Generator zu verwenden, bevor Sie **Rand**aufrufen.

Die **Rand** -Funktion generiert eine bekannte Sequenz und ist nicht für die Verwendung als Kryptografiefunktion geeignet. Verwenden Sie zum Generieren einer kryptografisch sicheren Zufallszahlengenerierung [rand_s](rand-s.md) oder die in der C++-Standard Bibliothek in [ \<Random>](../../standard-library/random.md)deklarierten Funktionen. Informationen dazu, was bei **Rand** falsch ist und wie \<Random> diese Mängel behandelt, finden Sie in diesem Video, das [als schädlich angesehen](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
