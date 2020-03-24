---
title: Compilerfehler C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165742"
---
# <a name="compiler-error-c3768"></a>Compilerfehler C3768

> die Adresse einer virtuellen vararg-Funktion in reinem verwaltetem Code kann nicht übernommen werden.

## <a name="remarks"></a>Bemerkungen

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt.

Beim Kompilieren mit **/clr: pure**können Sie die Adresse einer virtuellen `vararg` Funktion nicht übernehmen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3768 generiert:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```
