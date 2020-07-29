---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: a0108cff3d6b98fd929b7888d2ad718e7b6b3a64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213254"
---
# <a name="restrict"></a>restrict

**Microsoft-spezifisch**

**`restrict`** Weist den Compiler an, dass die Funktion ein Objekt zurückgibt, das keinen *Alias*hat, d. h. von anderen Zeigern referenziert, wenn Sie auf eine Funktionsdeklaration oder-Definition angewendet wird, die einen Zeigertyp zurückgibt. Dies ermöglicht es dem Compiler, zusätzliche Optimierungen auszuführen.

## <a name="syntax"></a>Syntax

> **`__declspec(restrict)`***pointer_return_type* - *Funktion*();

## <a name="remarks"></a>Bemerkungen

Der Compiler gibt weiter **`__declspec(restrict)`** . Die CRT-Funktion hat z. b. `malloc` eine **`__declspec(restrict)`** Dekoration. Daher geht der Compiler davon aus, dass Zeiger, die auf Speicherpositionen von initialisiert `malloc` werden, auch nicht durch zuvor vorhandene Zeiger als Alias behandelt werden.

Der Compiler überprüft nicht, ob der zurückgegebene Zeiger tatsächlich ein Alias ist. Es liegt in der Verantwortung des Entwicklers, sicherzustellen, dass das Programm keinen Zeiger Alias verwendet, der mit der **Einschränkung __declspec** Modifizierer gekennzeichnet ist.

Eine ähnliche Semantik für Variablen finden Sie unter [__restrict](../cpp/extension-restrict.md).

Eine andere Anmerkung, die für Aliasing innerhalb einer Funktion gilt, finden Sie unter [__declspec (noalias)](../cpp/noalias.md).

Weitere Informationen über das **`restrict`** Schlüsselwort, das Teil C++ amp ist, finden Sie unter [einschränken (C++ amp)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Verwendung von veranschaulicht **`__declspec(restrict)`** .

Wenn **`__declspec(restrict)`** auf eine Funktion angewendet wird, die einen Zeiger zurückgibt, weist dies den Compiler darauf hin, dass der Speicher, auf den der Rückgabewert zeigt, kein Alias ist. In diesem Beispiel sind die Zeiger `mempool` und `memptr` Global, sodass der Compiler nicht sicherstellen kann, dass der Speicher, auf den Sie verweisen, kein Alias ist. Allerdings werden Sie `ma` in und dem Aufrufer `init` auf eine Weise verwendet, die Speicher zurückgibt, auf den nicht anderweitig vom Programm verwiesen wird, sodass **__decslpec (einschränken)** verwendet wird, um den Optimierer zu unterstützen. Dies ähnelt der Art und Weise, wie die CRT-Header Zuordnungs Funktionen wie z. b. `malloc` verwenden **`__declspec(restrict)`** , um anzugeben, dass Sie immer Arbeitsspeicher zurückgeben, für den keine Aliasing durch vorhandene Zeiger

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec (noalias)](../cpp/noalias.md)
