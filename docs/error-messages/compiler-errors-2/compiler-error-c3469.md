---
title: Compilerfehler C3469
ms.date: 11/04/2016
f1_keywords:
- C3469
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
ms.openlocfilehash: 32d61e022de47b95ce3e84f1575cc090c74d70e3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742800"
---
# <a name="compiler-error-c3469"></a>Compilerfehler C3469

'typ': Eine generische Klasse kann nicht weitergeleitet werden.

Typweiterleitung kann nicht für generische Klassen verwendet werden.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Komponente erstellt.

```cpp
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

Im folgenden Beispiel wird C3466 generiert:

```cpp
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
