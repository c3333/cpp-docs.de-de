---
title: Compilerwarnung (Stufe 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 66e782c2fbb9c39c6a189de496cd0dcb4f1f4991
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218077"
---
# <a name="compiler-warning-level-4-c4559"></a>Compilerwarnung (Stufe 4) C4559

> "*Function*": Neudefinition; die Funktion gewinnt __declspec (*Modifizierer*).

## <a name="remarks"></a>Bemerkungen

Eine Funktion wurde neu definiert oder erneut deklariert, und die zweite Definition oder Deklaration hat einen **`__declspec`** Modifizierer (*Modifizierer*) hinzugefügt. Diese Warnung dient nur zu Informationszwecken. Löschen Sie eine der Definitionen, um diese Warnung zu beheben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4559 generiert:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
