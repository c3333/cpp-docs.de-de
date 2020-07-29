---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: ef1a2045a20070b667d416175826e5377fe30ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215984"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Microsoft-spezifisch**

Schreibt 32-Bit-Daten an einen Speicherort, ohne die Caches zu verschmutzen.

## <a name="syntax"></a>Syntax

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Parameter

*Entwickelt*\
vorgenommen Ein Zeiger auf den Speicherort, an den die Quelldaten geschrieben werden.

*Ausgangs*\
in Eine 128-Bit-Zahl, die den Wert enthält, der **`float`** in den untersten 32 Bits geschrieben werden soll.

## <a name="return-value"></a>Rückgabewert

Keine.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die systeminterne Generierung generiert die- `movntss` Anweisung. Um die Hardwareunterstützung für diese Anweisung zu ermitteln, müssen Sie die systeminterne Funktion `__cpuid` mit `InfoType=0x80000001` und das-Bit 6 von abrufen `CPUInfo[2] (ECX)` . Dieses Bit ist 1, wenn die Anweisung unterstützt wird, und andernfalls 0.

Wenn Sie Code ausführen, der die systeminterne Funktion auf Hardware verwendet, die `_mm_stream_ss` die-Anweisung nicht unterstützt `movntss` , sind die Ergebnisse unvorhersehbar.

## <a name="example"></a>Beispiel

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Ende Microsoft-spezifisch**

Teile Copyright 2007 von Advanced Micro Devices, Inc. Alle Rechte vorbehalten. Mit Berechtigung von Advanced Micro Devices, Inc.

## <a name="see-also"></a>Weitere Informationen

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
