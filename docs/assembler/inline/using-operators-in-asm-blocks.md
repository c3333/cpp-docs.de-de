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
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169096"
---
# <a name="using-operators-in-__asm-blocks"></a>Verwenden von Operatoren in __asm-Blöcken

**Microsoft-spezifisch**

Ein `__asm`-Block kann C oder C++ bestimmte Operatoren, z. b. den **<<** -Operator, nicht verwenden. Operatoren, die von C und MASM gemeinsam genutzt werden, z. b. der \*-Operator, werden jedoch als assemblysprachoperatoren interpretiert. So werden z. b. außerhalb eines `__asm` Blocks eckige Klammern ( **[]** ) als einschließende Array Index interpretiert, das C automatisch auf die Größe eines Elements im Array skaliert. In einem `__asm`-Block werden Sie als MASM-Index Operator betrachtet, der einen nicht skalierten Byte Offset von einem beliebigen Datenobjekt oder einer Bezeichnung (nicht nur ein Array) ergibt. Der folgende Code veranschaulicht den Unterschied:

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

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C oder C++ in __asm-Blöcken](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
