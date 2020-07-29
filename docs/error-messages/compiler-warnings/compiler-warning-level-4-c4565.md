---
title: Compilerwarnung (Stufe 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195979"
---
# <a name="compiler-warning-level-4-c4565"></a>Compilerwarnung (Stufe 4) C4565

> "*Function*": Neudefinition; das Symbol wurde zuvor mit __declspec (*Modifizierer*) deklariert.

## <a name="remarks"></a>Bemerkungen

Ein Symbol wurde neu definiert oder erneut deklariert, und die zweite Definition oder Deklaration enthielt nicht einen **`__declspec`** Modifizierer (*Modifizierer*). Diese Warnung dient nur zu Informationszwecken. Löschen Sie eine der Definitionen, um diese Warnung zu beheben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4565 generiert:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
