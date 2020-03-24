---
title: Compilerwarnung (Stufe 1) C4944
ms.date: 11/04/2016
f1_keywords:
- C4944
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
ms.openlocfilehash: f9db36d52647b55c292a15ca724822f8b8b47e9c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199199"
---
# <a name="compiler-warning-level-1-c4944"></a>Compilerwarnung (Stufe 1) C4944

'symbol': Das Symbol kann nicht aus 'assembly1' importiert werden, da 'symbol' im aktuellen Gültigkeitsbereich bereits vorhanden ist

Es wurde ein Symbol in einer Quellcodedatei definiert, und dann wurde in einer #using-Anweisung auf eine Assembly verwiesen, die das Symbol ebenfalls definiert. Das Symbol in der Assembly wird ignoriert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Komponente mit einem Typ namens 'ClassA' erstellt.

```csharp
// C4944.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

## <a name="example"></a>Beispiel

In den folgenden Beispielen wird C4944 generiert:

```cpp
// C4944b.cpp
// compile with: /clr /W1
class ClassA {
public:
   int u;
};

#using "C4944.dll"   // C4944 ClassA also defined C4944.dll

int main() {
   ClassA * x = new ClassA();
   x->u = 9;
   System::Console::WriteLine(x->u);
}
```
