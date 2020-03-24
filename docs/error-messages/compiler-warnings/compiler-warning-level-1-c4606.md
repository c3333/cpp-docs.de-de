---
title: Compilerwarnung (Stufe 1) C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: 9b38e9670157fd15dc7c4b6a96ced7ad40c43e34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185996"
---
# <a name="compiler-warning-level-1-c4606"></a>Compilerwarnung (Stufe 1) C4606

\#pragma-Warnung: "Warning_number" wird ignoriert. Code Analyse Warnungen sind keinen Warn Stufen zugeordnet.

Bei Code Analyse Warnungen werden nur `error`, `once`und `default` mit dem [Warning](../../preprocessor/warning.md) -Pragma unterstützt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4606 generiert.

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```
