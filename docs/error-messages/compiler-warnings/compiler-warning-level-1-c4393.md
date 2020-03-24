---
title: Compilerwarnung (Stufe 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: edc09bd48614abe3ea06d4365cb55110f8b9956b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162711"
---
# <a name="compiler-warning-level-1-c4393"></a>Compilerwarnung (Stufe 1) C4393

"var": die Konstante hat keine Auswirkung auf den literaldatenmember. erten

Ein [literaldatenmember](../../extensions/literal-cpp-component-extensions.md) wurde auch als konstant angegeben.  Da ein literaldatenmember konstant impliziert, müssen Sie der Deklaration keine Konstanten hinzufügen.

Im folgenden Beispiel wird C4393 generiert:

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
