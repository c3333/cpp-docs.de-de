---
title: Compilerwarnung (Stufe 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 17a33f7c55fa2825eae1c7d8b9d8ab78e4ed5274
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225331"
---
# <a name="compiler-warning-level-1-c4807"></a>Compilerwarnung (Stufe 1) C4807

"Operation": Unsichere Kombination von Typ "Typ" und signiertem Bitfeld des Typs "Typ"

Diese Warnung wird generiert, wenn ein Bitfeld mit einem Bit mit Vorzeichen mit einer Variablen verglichen wird **`bool`** . Da ein ein-Bit-Bitfeld mit Vorzeichen nur die Werte-1 oder 0 enthalten kann, ist es gefährlich, es mit zu vergleichen **`bool`** . Es werden keine Warnungen für das Mischen **`bool`** und ein Bitfeld ohne Vorzeichen generiert, da Sie mit identisch sind **`bool`** und nur 0 oder 1 enthalten können.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4807 generiert:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
