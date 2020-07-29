---
title: Compilerfehler C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 6b61904fac09145ba749138a730603fcfdbb862d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223381"
---
# <a name="compiler-error-c3737"></a>Compilerfehler C3737

"Delegat": ein Delegat hat möglicherweise keine explizite Aufruf Konvention.

Sie können die [Aufruf Konvention](../../cpp/calling-conventions.md) für nicht angeben **`delegate`** .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3737 generiert:

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
