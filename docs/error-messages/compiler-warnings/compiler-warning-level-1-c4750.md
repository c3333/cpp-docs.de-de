---
title: Compilerwarnung (Stufe 1) C4750
description: Beschreibt die MSVC-Compilerwarnung C4750 zu einem möglichen Stapelüberlauf.
ms.date: 07/08/2020
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 9a22bdda407b02b8723b7198d62289d39f62792d
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180967"
---
# <a name="compiler-warning-level-1-c4750"></a>Compilerwarnung (Stufe 1) C4750

> '*Identifier*': Funktion mit _alloca () Inline in eine Schleife

## <a name="remarks"></a>Bemerkungen

Die "*Identifier*"-Funktion erzwingt eine Inline Erweiterung der [`_alloca`](../../c-runtime-library/reference/alloca.md) Funktion innerhalb einer Schleife, die bei der Ausführung der Schleife einen Stapelüberlauf verursachen kann.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass die "*Identifier*"-Funktion nicht mit dem [`__forceinline`](../../cpp/inline-functions-cpp.md) Spezifizierer geändert wird.

1. Stellen Sie sicher, dass die "*Identifier*"-Funktion keine [`_alloca`](../../c-runtime-library/reference/alloca.md) in einer Schleife enthaltene Funktion enthält.

1. Geben Sie den [`/O1`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) [`/O2`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) [`/Ox`](../../build/reference/ox-full-optimization.md) Kompilierungs Schalter,, oder nicht an [`/Og`](../../build/reference/og-global-optimizations.md) .

1. Platzieren [`_alloca`](../../c-runtime-library/reference/alloca.md) Sie die Funktion in einer [Try-außer-Anweisung](../../cpp/try-except-statement.md) , die einen Stapelüberlauf abfängt.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `MyFunction` in einer Schleife aufgerufen und `MyFunction` ruft die `_alloca` -Funktion auf. Der `__forceinline` -Modifizierer bewirkt die Inlineerweiterung der `_alloca` -Funktion.

```cpp
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>Weitere Informationen

[_alloca](../../c-runtime-library/reference/alloca.md)
