---
title: 'Gewusst wie: Angeben eines out-Parameters'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 4bd6ad1d3009adcc124bdeb90d9d67de07112de2
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545444"
---
# <a name="how-to-specify-an-out-parameter"></a>Gewusst wie: Angeben eines out-Parameters

In diesem Beispiel wird gezeigt, wie angegeben wird, dass ein Funktionsparameter ein `out`-Parameter ist und wie diese Funktion C# von einem Programm aus aufgerufen wird.

Ein `out`-Parameter wird in C++ mithilfe von <xref:System.Runtime.InteropServices.OutAttribute> angegeben.

## <a name="example"></a>Beispiel

Der erste Teil dieses Beispiels erstellt eine C++ dll. Es definiert einen Typ, der eine Funktion mit einem `out`-Parameter enthält.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

Diese Quelldatei ist ein C# Client, der die C++ im vorherigen Beispiel erstellte Komponente verwendet.

```csharp
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
