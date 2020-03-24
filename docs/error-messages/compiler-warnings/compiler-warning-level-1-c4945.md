---
title: Compilerwarnung (Stufe 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 15a78877dbe70a7f95674092984546219e6a1c78
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199124"
---
# <a name="compiler-warning-level-1-c4945"></a>Compilerwarnung (Stufe 1) C4945

' Symbol ': das Symbol kann nicht aus ' Assembly2 ' importiert werden: da ' Symbol ' bereits aus einer anderen Assembly ' Assembly1 ' importiert wurde.

Ein Symbol wurde aus einer referenzierten Assembly importiert, aber dieses Symbol wurde bereits aus einer anderen Assembly importiert, auf die verwiesen wird. Verweisen Sie entweder nicht auf eine der Assemblys, oder lassen Sie den Symbolnamen in einer der Assemblys geändert.

In den folgenden Beispielen wird C4945 generiert.

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Und dann

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Und dann

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```
