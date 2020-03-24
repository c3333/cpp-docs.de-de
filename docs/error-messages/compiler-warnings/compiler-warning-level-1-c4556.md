---
title: Compilerwarnung (Stufe 1) C4556
ms.date: 08/27/2018
f1_keywords:
- C4556
helpviewer_keywords:
- C4556
ms.assetid: e4c0e296-b747-4db1-9608-30b8b74feac2
ms.openlocfilehash: 501d79a8a86fcd3e2d8ba08dc2f03488f9abb827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162308"
---
# <a name="compiler-warning-level-1-c4556"></a>Compilerwarnung (Stufe 1) C4556

> der Wert des systeminternen unmittelbaren Arguments '*value*' liegt außerhalb des gültigen Bereichs '*klein gebunden* - *obere Grenze*'.

## <a name="remarks"></a>Bemerkungen

Eine systeminterne Funktion stimmt mit einer Hardware Anweisung überein. Die Hardware Anweisung verfügt über eine Fixed-Anzahl von Bits, um die Konstante zu codieren. Wenn der *Wert* außerhalb des gültigen Bereichs liegt, wird er nicht ordnungsgemäß codiert. Der Compiler verkürzt die zusätzlichen Bits.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4556 generiert:

```cpp
// C4556.cpp
// compile with: /W1
// processor: x86 IPF
#include <xmmintrin.h>

void test()
{
   __m64 m;
   _m_pextrw(m, 5);   // C4556
}

int main()
{
}
```
