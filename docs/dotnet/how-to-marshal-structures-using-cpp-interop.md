---
title: 'Gewusst wie: Marshallen von Strukturen mit C++-Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 8ca53761647c1f3d5ea059ddf381cb334cd2a993
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413839"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Gewusst wie: Marshallen von Strukturen mit C++-Interop

In diesem Thema wird ein Aspekt der Visual C++ Interoperabilität veranschaulicht. Weitere Informationen finden Sie unter [using C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. diese Funktionen werden jedoch auf die gleiche Weise interagiert, wenn Sie in separaten Dateien definiert werden. Dateien, die nur nicht verwaltete Funktionen enthalten, müssen nicht mit/CLR kompiliert werden [(Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-pass-structure-from-managed-to-unmanaged-function"></a>Beispiel: übergeben der Struktur von der verwalteten an die nicht verwaltete Funktion

Im folgenden Beispiel wird veranschaulicht, wie eine Struktur von einer verwalteten an eine nicht verwaltete Funktion übergeben wird, sowohl nach Wert als auch nach Verweis. Da die Struktur in diesem Beispiel nur einfache, systeminterne Datentypen enthält (siehe [blitfähige und nicht blitfähige Typen](/dotnet/framework/interop/blittable-and-non-blittable-types)), ist kein spezielles Marshalling erforderlich. Informationen zum Mars Hallen von nicht blitfähigen Strukturen, z. b. solche, die Zeiger enthalten, finden Sie unter Gewusst [wie: Mars Hallen von eingebetteten Zeigern mithilfe von C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

```cpp
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example-pass-structure-from-unmanaged-to-managed-function"></a>Beispiel: Struktur von nicht verwaltetem an verwaltete Funktion übergeben

Im folgenden Beispiel wird veranschaulicht, wie eine Struktur von einer nicht verwalteten an eine verwaltete Funktion als Wert und als Verweis übergeben wird. Da die Struktur in diesem Beispiel nur einfache, systeminterne Datentypen enthält (siehe [blitfähige und nicht blitfähige Typen](/dotnet/framework/interop/blittable-and-non-blittable-types)), ist keine besondere Marshalling erforderlich. Informationen zum Mars Hallen von nicht blitfähigen Strukturen, z. b. solche, die Zeiger enthalten, finden Sie unter Gewusst [wie: Mars Hallen von eingebetteten Zeigern mithilfe von C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

```cpp
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
