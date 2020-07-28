---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: ec639004884d022fe6a827c2ec31d3201ea04657
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214216"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Microsoft-spezifisch**

Schreibt 64-Bit-Daten an einen Speicherort, ohne die Caches zu verschmutzen.

## <a name="syntax"></a>Syntax

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>Parameter

*Dest*\
vorgenommen Ein Zeiger auf den Speicherort, an den die Quelldaten geschrieben werden.

*Ausgangs*\
in Ein 128-Bit-Wert, der den **`double`** Wert enthält, der in seinen untersten 64 Bits geschrieben werden soll.

## <a name="return-value"></a>Rückgabewert

Keine.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die systeminterne Generierung generiert die- `movntsd` Anweisung. Um die Hardwareunterstützung für diese Anweisung zu ermitteln, müssen Sie die systeminterne Funktion `__cpuid` mit `InfoType=0x80000001` und das-Bit 6 von abrufen `CPUInfo[2] (ECX)` . Dieses Bit ist 1, wenn die Hardware diese Anweisung unterstützt, andernfalls 0.

Wenn Sie Code ausführen, der die systeminterne Funktion auf Hardware verwendet, die `_mm_stream_sd` die-Anweisung nicht unterstützt `movntsd` , sind die Ergebnisse unvorhersehbar.

## <a name="example"></a>Beispiel

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**Ende Microsoft-spezifisch**

Teile Copyright 2007 von Advanced Micro Devices, Inc. Alle Rechte vorbehalten. Mit Berechtigung von Advanced Micro Devices, Inc.

## <a name="see-also"></a>Weitere Informationen

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
