---
title: Compilerwarnung (Stufe 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198717"
---
# <a name="compiler-warning-level-3-c4334"></a>Compilerwarnung (Stufe 3) C4334

'Operator': Ergebnis der 32-Bit-Verschiebung wurde implizit zu 64 Bit konvertiert (war eine 64-Bit-Verschiebung vorgesehen?)

Das Ergebnis der 32-Bit-Verschiebung wurde implizit nach 64-Bit konvertiert, und der Compiler vermutet, dass eine 64-Bit-Verschiebung vorgesehen war.  Zur Behebung des Problems verwenden Sie eine 64-Bit-Verschiebung, oder wandeln Sie das Ergebnis der Verschiebung explizit in 64-Bit um.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4334 generiert.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
