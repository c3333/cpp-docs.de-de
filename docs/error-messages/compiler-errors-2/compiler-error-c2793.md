---
title: Compilerfehler C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: faf87334f1a98661078341a4d7dc11280802a376
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220209"
---
# <a name="compiler-error-c2793"></a>Compilerfehler C2793

"Token": Unerwartetes Token nach "::", Bezeichner oder Schlüsselwort "Operator" erwartet.

Die einzigen Token, die befolgt `__super::` werden können, sind ein Bezeichner oder das-Schlüsselwort **`operator`** .

Im folgenden Beispiel wird C2793 generiert.

```cpp
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```
