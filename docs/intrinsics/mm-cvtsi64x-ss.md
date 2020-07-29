---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: a8227fcb482267946ea7ba08ee352c43e1ac6f6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217999"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Microsoft-spezifisch**

Generiert die erweiterte x64-Version der 64-Bit-Ganzzahl mit Gleit Komma Zahlen in skalare Gleit Komma Wert Anweisung mit einfacher Genauigkeit `cvtsi2ss` .

## <a name="syntax"></a>Syntax

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>Parameter

*ein*\
in Eine-Struktur, die **`__m128`** vier Gleit Komma Werte mit einfacher Genauigkeit enthält.

*b*\
in Eine 64-Bit-Ganzzahl, die in einen Gleit Komma Wert konvertiert werden soll.

## <a name="return-value"></a>Rückgabewert

Eine- **`__m128`** Struktur, deren erster Gleit Komma Wert das Ergebnis der Konvertierung ist. Die anderen drei Werte werden unverändert aus *einer*kopiert.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|x64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die- **`__m128`** Struktur stellt ein XMM-Register dar, sodass die systeminterne Funktion den Wert *b* aus dem System Arbeitsspeicher in ein XMM-Register verschieben kann.

Diese Routine ist nur als systeminterne Funktion verfügbar.

## <a name="example"></a>Beispiel

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__m128](../cpp/m128.md)\
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
