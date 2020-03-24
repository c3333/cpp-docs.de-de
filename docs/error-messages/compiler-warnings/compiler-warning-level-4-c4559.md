---
title: Compilerwarnung (Stufe 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198340"
---
# <a name="compiler-warning-level-4-c4559"></a>Compilerwarnung (Stufe 4) C4559

> "*Function*": Neudefinition; die Funktion gewinnt __declspec (*Modifizierer*).

## <a name="remarks"></a>Bemerkungen

Eine Funktion wurde neu definiert oder erneut deklariert, und die zweite Definition oder Deklaration hat einen **__declspec** Modifizierer (*Modifizierer*) hinzugefügt. Diese Warnung dient nur zu Informationszwecken. Löschen Sie eine der Definitionen, um diese Warnung zu beheben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4559 generiert:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
