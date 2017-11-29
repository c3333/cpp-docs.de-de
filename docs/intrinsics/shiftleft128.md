---
title: __shiftleft128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __shiftleft128
dev_langs: C++
helpviewer_keywords: __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 245948bf090990590b22c3b790858f8cffe00427
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="shiftleft128"></a>__shiftleft128
**Microsoft-spezifisch**  
  
 Verschiebt eine 128-Bit-Menge, dargestellt als zwei 64-Bit-Mengen `LowPart` und `HighPart`, um eine angegebene Anzahl von Bits, die durch `Shift` definiert wird, nach links und gibt die unteren 64 Bits des Ergebnisses zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
unsigned __int64 __shiftleft128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `LowPart`  
 Die unteren 64 Bits der zu verschiebenden 128-Bit-Menge.  
  
 [in] `HighPart`  
 Die oberen 64 Bits der zu verschiebenden 128-Bit-Menge.  
  
 [in] `Shift`  
 Die Anzahl der zu verschiebenden Bits.  
  
## <a name="return-value"></a>Rückgabewert  
 Die oberen 64 Bits des Ergebnisses.  
  
## <a name="requirements"></a>Anforderungen  
  
|Systemintern|Architektur|  
|---------------|------------------|  
|`__shiftleft128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Headerdatei** \<intrin.h >  
  
## <a name="remarks"></a>Hinweise  
 Der `Shift`-Wert ist immer modulo 64. So verschiebt z. B. beim Aufrufen von `__shiftleft128(1, 0, 64)` die Funktion die `0`-Bits des unteren Teils nach links und gibt einen oberen Teil von `0` und nicht von `1` zurück, wie man annehmen könnte.  
  
## <a name="example"></a>Beispiel  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
```Output  
0x100000000000000001 << 1 = 0x200000000000000002  
0x100000000000000001 >> 1 = 0x080000000000000000  
```  
  
**Ende Microsoft-spezifisch**  
  
## <a name="see-also"></a>Siehe auch  
 [__shiftright128](../intrinsics/shiftright128.md)   
 [Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)