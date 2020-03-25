---
title: Compilerwarnung C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: df6fc88ffe98dd2b4a3129800c7881f26d4f625b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164819"
---
# <a name="compiler-warning-c4986"></a>Compilerwarnung C4986

"Function": die Ausnahme Spezifikation stimmt nicht mit der vorherigen Deklaration.

Diese Warnung kann generiert werden, wenn eine Ausnahme Spezifikation in einer Deklaration und nicht in der anderen vorliegt.

Standardmäßig ist C4986 auf OFF eingestellt. Weitere Informationen finden Sie unter [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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
