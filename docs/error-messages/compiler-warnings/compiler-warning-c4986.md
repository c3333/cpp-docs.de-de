---
title: Compilerwarnung C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: ae782ea0a11bd72c867ea9532a62d0b14cd98453
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684391"
---
# <a name="compiler-warning-c4986"></a>Compilerwarnung C4986

"Function": die Ausnahme Spezifikation stimmt nicht mit der vorherigen Deklaration.

Diese Warnung kann generiert werden, wenn eine Ausnahme Spezifikation in einer Deklaration und nicht in der anderen vorliegt.

Standardmäßig ist C4986 auf OFF eingestellt. Weitere Informationen finden Sie unter [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C4986 generiert.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

Im folgenden Beispiel wird diese Warnung vermieden.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
