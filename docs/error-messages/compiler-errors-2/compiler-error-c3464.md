---
title: Compilerfehler C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: ddfd795465af559885ad05775d87d6188f2f13a8
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742852"
---
# <a name="compiler-error-c3464"></a>Compilerfehler C3464

"Typ" Ein geschachtelter Typ kann nicht weitergeleitet werden.

Weiterleiten von Typen funktioniert nicht bei geschachtelten Typen.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Komponente erstellt.

```cpp
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

Im folgenden Beispiel wird C3464 generiert:

```cpp
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
