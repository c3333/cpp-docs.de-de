---
title: Compilerwarnung C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164988"
---
# <a name="compiler-warning-c4950"></a>Compilerwarnung C4950

'type_or_member': als veraltet markiert.

Ein Member oder Typ wurde mit dem <xref:System.ObsoleteAttribute>-Attribut als veraltet markiert.

C4950 wird immer als Fehler ausgegeben. Sie können diese Warnung mithilfe der [Warning](../../preprocessor/warning.md) -pragma-Direktive oder der [/WD](../../build/reference/compiler-option-warning-level.md) -Compileroption deaktivieren.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4950 generiert.

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
