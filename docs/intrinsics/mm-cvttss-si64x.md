---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 6d920a5c59cacb23c7fb155c7ac8e813a9b0e8d0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217986"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Microsoft-spezifisch**

Gibt die erweiterte x64-Version der Konvertierung mit einer Gleit Komma Zahl mit einfacher Genauigkeit und einer Gleit Komma Zahl mit einfacher Genauigkeit in 64-Bit- `cvttss2si` Anweisung () aus.

## <a name="syntax"></a>Syntax

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parameter

*Wert*\
in Eine **`__m128`** -Struktur mit Gleit Komma Werten mit einfacher Genauigkeit.

## <a name="return-value"></a>Rückgabewert

Das Ergebnis der Konvertierung des ersten Gleit Komma Werts in eine 64-Bit-Ganzzahl.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`_mm_cvttss_si64x`|x64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die intrinsische unterscheidet sich von `_mm_cvtss_si64x` nur darin, dass ungenaue Konvertierungen in Richtung NULL abgeschnitten werden. Da die- **`__m128`** Struktur ein XMM-Register darstellt, verschiebt die generierte Anweisung Daten aus einem XMM-Register in den Systemspeicher.

Diese Routine ist nur als systeminterne Funktion verfügbar.

## <a name="example"></a>Beispiel

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__m128](../cpp/m128.md)\
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
