---
title: Argumentbezogene Namenssuche (Koenig) in Funktionen
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 88811e8070fdfe398bc12734221dee772515d8bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190535"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Argumentbezogene Namenssuche (Koenig) in Funktionen

Der Compiler kann eine argumentbezogene Namenssuche verwenden, um die Definition eines nicht qualifizierten Funktionsaufrufs zu suchen. Die argumentbezogene Namenssuche wird auch Koenig-Suche genannt. Der Typ jedes Arguments in einem Funktionsaufruf wird innerhalb einer Hierarchie von Namespaces, Klassen, Strukturen, Unions oder Vorlagen definiert. Wenn Sie einen nicht qualifizierten [postfix](../cpp/postfix-expressions.md) -Funktions aufzurufen angeben, sucht der Compiler in der Hierarchie, die dem jeweiligen Argumenttyp zugeordnet ist, nach der Funktionsdefinition.

## <a name="example"></a>Beispiel

Im Beispiel stellt der Compiler fest, dass Funktion `f()` ein Argument `x` akzeptiert. Argument `x` ist vom Typ `A::X`, der im Namespace `A` definiert ist. Der Compiler durchsucht Namespace `A` und findet eine Definition für die `f()`-Funktion, die ein Argument des Typs `A::X` akzeptiert.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```
