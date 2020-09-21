---
title: Compilerfehler C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: dd7046fcf87a6b8f095092ef0de4b94326151e87
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742826"
---
# <a name="compiler-error-c3467"></a>Compilerfehler C3467

'typ': Dieser Typ wurde bereits weitergeleitet.

Der Compiler hat mehr als eine Vorwärts-Typdeklaration für den gleichen Typ gefunden. Es ist nur eine Deklaration pro Typ zulässig.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Komponente erstellt.

```cpp
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

Im folgenden Beispiel wird C3467 generiert:

```cpp
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```
