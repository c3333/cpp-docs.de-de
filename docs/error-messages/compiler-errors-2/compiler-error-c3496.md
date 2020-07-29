---
title: Compilerfehler C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 993d391f28a59afc8926748f2e6f34ab441657dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228855"
---
# <a name="compiler-error-c3496"></a>Compilerfehler C3496

"this" wird immer nach Wert erfasst: "&" wird ignoriert.

Der Zeiger kann nicht als **`this`** Verweis erfasst werden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Erfassen Sie den **`this`** Zeiger nach Wert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3496 generiert, weil ein Verweis auf den- **`this`** Zeiger in der Erfassungs Liste eines Lambda-Ausdrucks angezeigt wird:

```cpp
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
