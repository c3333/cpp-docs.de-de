---
title: Compilerfehler C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 0d49eae823eb64f97e7276d432e161b3de21d725
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510068"
---
# <a name="compiler-error-c3734"></a>Compilerfehler C3734

'class': Eine verwaltete oder WinRT-Klasse kann kein „coclass“-Attribut sein.

Das [Co-Klasse](../../windows/attributes/coclass.md) -Attribut kann nicht für verwaltete oder WinRT-Klassen verwendet werden.

Im folgenden Beispiel wird C3734 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
