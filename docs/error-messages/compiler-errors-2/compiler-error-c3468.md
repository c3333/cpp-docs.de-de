---
title: Compilerfehler C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: f22a01c5c26a55a5908c20f3b123971fadd43544
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742813"
---
# <a name="compiler-error-c3468"></a>Compilerfehler C3468

"Typ": Sie können einen Typ nur an eine Assembly weiterleiten:

`file`ist keine Assembly.

Es können nur Typen in einer Assembly weitergeleitet werden.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein Modul erstellt.

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

Im folgenden Beispiel wird C3468 generiert:

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
