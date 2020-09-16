---
title: _InterlockedAdd intrinsische Funktionen
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: efe1444273f17c8f0544d2c51b98923169032e61
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683896"
---
# <a name="_interlockedadd-intrinsic-functions"></a>_InterlockedAdd intrinsische Funktionen

**Microsoft-spezifisch**

Diese Funktionen führen eine atomarische Addition aus, mit der sichergestellt wird, dass der Vorgang erfolgreich abgeschlossen wird, wenn mehr als ein Thread auf eine freigegebene Variable zugreifen kann.

## <a name="syntax"></a>Syntax

```C
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>Parameter

*Addend*\
[in, out] Zeiger auf die Ganzzahl, die hinzugefügt werden soll. ersetzt durch das Ergebnis der Addition.

*Wert*\
in Der hinzu zufügende Wert.

## <a name="return-value"></a>Rückgabewert

Beide Funktionen geben das Ergebnis der Addition zurück.

## <a name="requirements"></a>Anforderungen

|Intrinsic|Aufbau|
|---------------|------------------|
|`_InterlockedAdd`|Arm, ARM64|
|`_InterlockedAdd_acq`|Arm, ARM64|
|`_InterlockedAdd_nf`|Arm, ARM64|
|`_InterlockedAdd_rel`|Arm, ARM64|
|`_InterlockedAdd64`|Arm, ARM64|
|`_InterlockedAdd64_acq`|Arm, ARM64|
|`_InterlockedAdd64_nf`|Arm, ARM64|
|`_InterlockedAdd64_rel`|Arm, ARM64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die Versionen dieser Funktionen mit den Suffixen `_acq` oder `_rel` führen eine ineinander greifende Addition gemäß der Semantiken zum Abrufen oder Freigeben durch. Das Abrufen der *Semantik* bedeutet, dass das Ergebnis des Vorgangs für alle Threads und Prozessoren sichtbar gemacht wird, bevor spätere Speicher Lese-und Schreibvorgänge ausgeführt werden. „Acquire“ ist bei der Eingabe eines kritischen Abschnitts nützlich. Die *releasesemantik* bedeutet, dass alle Speicher Lese-und-Schreibvorgänge für alle Threads und Prozessoren sichtbar gemacht werden, bevor das Ergebnis des Vorgangs selbst sichtbar gemacht wird. „Release“ ist beim Verlassen eines kritischen Abschnitts nützlich. Die intrinsischen Funktionen mit dem `_nf` Suffix ("No fence") fungieren nicht als Arbeitsspeicher Barriere.

Diese Routinen sind nur als systeminterne Funktionen verfügbar.

## <a name="examples"></a>Beispiele

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output"></a>Output

```Output
0xffffff00 0xff0000 0xffffff00
```

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output"></a>Output

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[Konflikte mit dem x86-Compiler](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
