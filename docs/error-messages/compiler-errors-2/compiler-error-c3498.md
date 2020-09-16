---
title: Compilerfehler C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: f1b978a585f3404cd3a881f25d6ef6a0f66b212d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686154"
---
# <a name="compiler-error-c3498"></a>Compilerfehler C3498

"var": Sie können keine Variable erfassen, die über einen verwalteten oder winrttype verfügt.

Sie können keine Variable erfassen, die einen verwalteten Typ oder einen Windows-Runtime-Typ in einem „lambda“ aufweist.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Übergeben Sie die verwaltete oder Windows-Runtime-Variable an die Parameterliste des Lambda-Ausdrucks.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3498 generiert, da eine Variable mit einem verwalteten Typ in der Erfassungsliste eines Lambdaausdrucks angezeigt wird:

```cpp
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

Im folgende Beispiel wird C3498 durch Übergeben der verwaltete Variablen `s` an die Parameterliste des Lambda-Ausdrucks aufgelöst:

```cpp
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
