---
title: Compilerfehler C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: c5195e0a9bba1bc9e5962f3d3ae1795bb098be3d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742878"
---
# <a name="compiler-error-c3461"></a>Compilerfehler C3461

'Typ': Nur ein verwalteter Typ kann weitergeleitet werden.

Die Typweiterleitung ist nur bei CLR-Typen möglich.  Weitere Informationen finden Sie unter [Klassen und Strukturen](../../extensions/classes-and-structs-cpp-component-extensions.md) .

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Komponente erstellt.

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

Im folgenden Beispiel wird C3461 generiert:

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
