---
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 70c1f4e8bfa426e858014a78febc424b473a89ae
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127871"
---
# `noalias`

**Microsoft-spezifisch**

**`noalias`** bedeutet, dass ein Funktions-oder Verweis auf den sichtbaren globalen Zustand nicht geändert wird, und dass nur der Speicher geändert wird, auf den *direkt* durch Zeiger Parameter verwiesen wird (Dereferenzierungen der ersten Ebene).

Wenn eine Funktion als kommentiert wird **`noalias`** , kann der Optimierer davon ausgehen, dass nur die Parameter selbst und nur Dereferenzierungen der ersten Ebene von Zeiger Parametern in der Funktion referenziert oder geändert werden.

Die-Anmerkung **`noalias`** gilt nur innerhalb des Texts der mit Anmerkungen versehene Funktion. Das Markieren einer Funktion als **`__declspec(noalias)`** wirkt sich nicht auf das Aliasing der von der Funktion zurückgegebenen Zeiger aus.

Weitere Anmerkungen, die sich auf Aliasing auswirken können, finden Sie unter [`__declspec(restrict)`](../cpp/restrict.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung von veranschaulicht **`__declspec(noalias)`** .

Wenn die Funktion `multiply` , die auf den Speicher zugreift **`__declspec(noalias)`** , kommentiert wird, weist Sie den Compiler an, dass diese Funktion den globalen Zustand nicht ändert, außer durch die Zeiger in der Parameterliste.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>Weitere Informationen

[`__declspec`](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
