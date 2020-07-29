---
title: Compilerwarnung (Stufe 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: aa2cdf0103a1ccc607f2e4a55e1d8f85bb8cc45d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233222"
---
# <a name="compiler-warning-level-1-c4804"></a>Compilerwarnung (Stufe 1) C4804

"Operation": unsichere Verwendung des Typs "bool" in Vorgang

Diese Warnung gilt für den Fall, dass Sie eine **`bool`** Variable oder einen Wert auf unerwartete Weise verwendet haben. Beispielsweise wird C4804 generiert, wenn Sie Operatoren wie den negativen unären Operator ( **-** ) oder den Komplement Operator ( `~` ) verwenden. Der Compiler wertet den Ausdruck aus.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4804 generiert:

```cpp
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```
