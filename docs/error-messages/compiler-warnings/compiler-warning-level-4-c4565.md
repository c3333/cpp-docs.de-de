---
title: Compilerwarnung (Stufe 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: 5eccb3c29da612a39f7fcdf4ef25dedb898c8d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198327"
---
# <a name="compiler-warning-level-4-c4565"></a>Compilerwarnung (Stufe 4) C4565

> "*Function*": Neudefinition; das Symbol wurde zuvor mit __declspec (*Modifizierer*) deklariert.

## <a name="remarks"></a>Bemerkungen

Ein Symbol wurde neu definiert oder neu deklariert, und die zweite Definition oder Deklaration hat nicht den `__declspec` Modifizierer (*Modifizierer*), anders als bei der ersten Definition oder Deklaration. Diese Warnung dient nur zu Informationszwecken. Löschen Sie eine der Definitionen, um diese Warnung zu beheben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4565 generiert:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
