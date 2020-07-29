---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: 6ae750f1a8825096ee30adb01768d5603ab23a01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219663"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Microsoft-spezifisch**

Verschiebt einen 64-Bit-Wert, der durch den ersten Parameter angegeben wird, um eine Anzahl von Bits, die durch den zweiten Parameter angegeben werden, nach rechts.

## <a name="syntax"></a>Syntax

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parameter

*Chel*\
in Der ganzzahlige 64-Bit-Wert für die Verschiebung nach rechts.

*nBit*\
in Die Anzahl der zu Verschiebe enden Bits, modulo 64 auf x64 und modulo 32 auf x86.

## <a name="return-value"></a>Rückgabewert

Die Maske, die von Bits verschoben wurde `nBit` .

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`__ll_rshift`|x86, x64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Wenn der zweite Parameter in x64 (32 auf x86) größer als 64 ist, wird diese Zahl in modulo 64 (32 auf x86) festgelegt, um die Anzahl der zu Verschiebe Bits zu bestimmen. Das `ll` Präfix gibt an, dass es sich um einen Vorgang auf **`long long`** , einen anderen Namen für, den ganzzahligen **`__int64`** Typ 64-Bit

## <a name="example"></a>Beispiel

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Output

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> Wenn `_ull_rshift` verwendet wurde, wäre das MSB des Rechts verschobenen Werts 0 (null), sodass das gewünschte Ergebnis bei einem negativen Wert nicht abgerufen wurde.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
