---
title: Verwenden von Operatoren in __asm-Blöcken
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: cdcfee20cfdc5a6dc315d00ef024d1616900a2e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191104"
---
# <a name="using-operators-in-__asm-blocks"></a>Verwenden von Operatoren in __asm-Blöcken

**Microsoft-spezifisch**

Ein- **`__asm`** Block kann keine C-oder C++-spezifischen Operatoren wie den- **<<** Operator verwenden. Operatoren, die von C und MASM gemeinsam genutzt werden, z. b. der- \* Operator, werden jedoch als assemblysprachoperatoren interpretiert. So werden z. b. außerhalb eines- **`__asm`** Blocks eckige Klammern (**[]**) als einschließende Array Indizes interpretiert, die C automatisch auf die Größe eines Elements im Array skaliert. Innerhalb eines- **`__asm`** Blocks werden Sie als MASM-Index Operator betrachtet, der einen nicht skalierten Byte Offset von einem beliebigen Datenobjekt oder einer beliebigen Bezeichnung (nicht nur ein Array) ergibt. Der folgende Code veranschaulicht den Unterschied:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

Der erste Verweis auf `array` wird nicht skaliert, aber der zweite ist. Beachten Sie, dass Sie den **Type** -Operator verwenden können, um die Skalierung basierend auf einer Konstanten zu erzielen. Beispielsweise sind die folgenden Anweisungen äquivalent:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Verwenden von C oder C++ in __asm Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
