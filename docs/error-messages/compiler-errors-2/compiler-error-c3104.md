---
title: Compilerfehler C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 5f72af3d7149db7362df9fa23ac5ad6c058c552b
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743463"
---
# <a name="compiler-error-c3104"></a>Compilerfehler C3104

Unzulässiges Attribut Argument

Sie haben ein ungültiges Argument für ein Attribut angegeben.

Weitere Informationen finden Sie unter [Attribut Parameter Typen](../../extensions/attribute-parameter-types-cpp-component-extensions.md) .

Dieser Fehler kann aufgrund von compilerübereinstimmungs-Aufgaben generiert werden, die für Visual Studio 2005 ausgeführt wurden: Wenn verwaltete Arrays an benutzerdefinierte Attribute übergeben werden, wird der Typ des Arrays nicht mehr aus der aggregierten Initialisierungs Liste abgeleitet. Der Compiler erfordert nun, dass Sie den Typ des Arrays und die Initialisiererliste angeben.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3104 generiert.

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

Im folgenden Beispiel wird C3104 generiert.

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
