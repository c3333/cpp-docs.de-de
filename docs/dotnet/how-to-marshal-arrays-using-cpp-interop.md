---
title: 'Gewusst wie: Marshallen von Arrays mit C++-Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: 0ccf71d40db0bc6989620d2ca126ce74311805da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413826"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>Gewusst wie: Marshallen von Arrays mit C++-Interop

In diesem Thema wird ein Aspekt der Visual C++ Interoperabilität veranschaulicht. Weitere Informationen finden Sie unter [using C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. diese Funktionen werden jedoch auf die gleiche Weise interagiert, wenn Sie in separaten Dateien definiert werden. Dateien, die nur nicht verwaltete Funktionen enthalten, müssen nicht mit/CLR kompiliert werden [(Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example-pass-managed-array-to-unmanaged-function"></a>Beispiel: Übergeben eines verwalteten Arrays an eine nicht verwaltete Funktion

Im folgenden Beispiel wird veranschaulicht, wie ein verwaltetes Array an eine nicht verwaltete Funktion übergeben wird. Die verwaltete Funktion verwendet [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , um Garbage Collection für das Array zu unterdrücken, bevor die nicht verwaltete Funktion aufgerufen wird. Durch die Bereitstellung der nicht verwalteten Funktion mit einem fixierten Zeiger auf den GC-Heap kann der Aufwand für das Erstellen einer Kopie des Arrays vermieden werden. Um zu veranschaulichen, dass die nicht verwaltete Funktion auf den GC-Heap Speicher zugreift, wird der Inhalt des Arrays geändert, und die Änderungen werden reflektiert, wenn die verwaltete Funktion die Steuerung fortsetzt.

```cpp
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example-pass-unmanaged-array-to-managed-function"></a>Beispiel: Übergeben eines nicht verwalteten Arrays an eine verwaltete Funktion

Im folgenden Beispiel wird veranschaulicht, wie ein nicht verwaltetes Array an eine verwaltete Funktion übergeben wird. Die verwaltete Funktion greift direkt auf den Array Speicher zu (anstatt ein verwaltetes Array zu erstellen und den Array Inhalt zu kopieren), sodass von der verwalteten Funktion vorgenommene Änderungen in der nicht verwalteten Funktion übernommen werden können, wenn die Steuerung wiedererlangt wird.

```cpp
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
