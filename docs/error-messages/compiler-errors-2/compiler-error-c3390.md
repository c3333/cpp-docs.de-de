---
title: Compilerfehler C3390
description: Microsoft C++-Compilerfehler C3390, seine Ursache und deren Behebung.
ms.date: 09/26/2020
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 467b379d7f5a349a217b566dc55b28d5fbd789da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414359"
---
# <a name="compiler-error-c3390"></a>Compilerfehler C3390

> '*type_arg*': Ungültiges Typargument für den generischen Parameter '*param*' von '*generic_type*' (generisch), muss ein Verweistyp sein.

Ein generischer Typ wurde fehlerhaft instanziiert. Überprüfen Sie die Typdefinition.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Generics](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im ersten Beispiel wird c# verwendet, um eine Komponente zu erstellen, die einen generischen Typ enthält. Dieser Typ weist bestimmte Einschränkungen auf, die beim Erstellen von generischen Typen in C++ nicht unterstützt werden/CLI. Weitere Informationen finden Sie unter [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Wenn die C3390.dll-Komponente verfügbar ist, wird im folgenden Beispiel C3390 generiert.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK - do this instead
}
```
