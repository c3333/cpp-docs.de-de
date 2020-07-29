---
title: Compilerfehler C2638
ms.date: 11/04/2016
f1_keywords:
- C2638
helpviewer_keywords:
- C2638
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
ms.openlocfilehash: 863537c60584ba836c6605f31249ada95a88a1bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212695"
---
# <a name="compiler-error-c2638"></a>Compilerfehler C2638

"Bezeichner": __based Modifizierer für Zeiger auf Member unzulässig

Der- **`__based`** Modifizierer kann nicht für Zeiger auf Member verwendet werden.

Im folgenden Beispiel wird C2638 generiert:

```cpp
// C2638.cpp
void *a;

class C {
public:
   int i;
   int j;
   int func();
};
int __based (a) C::* cpi = &C::i;  // C2638
int (__based (a) C::* cpf)() = &C::func; // c2638
```
