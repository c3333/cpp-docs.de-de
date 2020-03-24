---
title: Compilerwarnung (Stufe 1) C4384
ms.date: 11/04/2016
f1_keywords:
- C4384
helpviewer_keywords:
- C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
ms.openlocfilehash: 650f722affb6f1fe8c51e7a93619ecdef077fdb6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186958"
---
# <a name="compiler-warning-level-1-c4384"></a>Compilerwarnung (Stufe 1) C4384

\#Pragma "make_public" sollte nur im globalen Gültigkeitsbereich verwendet werden.

Das [make_public](../../preprocessor/make-public.md) -Pragma wurde falsch angewendet.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4384 generiert.

```cpp
// C4384.cpp
// compile with: /c /W1
namespace n {
   #pragma make_public(N::C)   // C4384
   namespace N {
      class C {};
   }
}
```
