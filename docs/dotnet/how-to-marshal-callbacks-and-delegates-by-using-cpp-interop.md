---
title: 'Gewusst wie: Marshallen von Rückrufen und Delegaten mit C++-Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 5d0427962ddb7d6409f07b99c0f618b340ee00df
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414294"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Gewusst wie: Marshallen von Rückrufen und Delegaten mit C++-Interop

In diesem Thema wird das Marshalling von Rückrufen und Delegaten (der verwalteten Version eines Rückrufs) zwischen verwaltetem und nicht verwaltetem Code mithilfe von Visual C++ veranschaulicht.

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. die Funktionen können jedoch auch in separaten Dateien definiert werden. Dateien, die nur nicht verwaltete Funktionen enthalten, müssen nicht mit [/CLR (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md)kompiliert werden.

## <a name="example-configure-unmanaged-api-to-trigger-managed-delegate"></a>Beispiel: Konfigurieren der nicht verwalteten API, um einen verwalteten Delegaten zu initiieren

Im folgenden Beispiel wird veranschaulicht, wie Sie eine nicht verwaltete API so konfigurieren, dass Sie einen verwalteten Delegaten auslöst. Ein verwalteter Delegat wird erstellt, und eine der Interop-Methoden, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A> , wird verwendet, um den zugrunde liegenden Einstiegspunkt für den Delegaten abzurufen. Diese Adresse wird dann an die nicht verwaltete Funktion weitergegeben, die Sie aufruft, ohne dass Sie wissen, dass Sie als verwaltete Funktion implementiert ist.

Beachten Sie, dass es möglich, aber nicht notwendig ist, den Delegaten mithilfe von [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) anzuheften, um zu verhindern, dass er vom Garbage Collector wieder gefunden oder verworfen wird. Der Schutz vor einem vorzeitigen Garbage Collection ist erforderlich, aber das Anhebungs bietet mehr Schutz als notwendig, da es die Erfassung verhindert, aber auch die Verlagerung verhindert.

Wenn ein Delegat durch einen Garbage Collection neu angeordnet wird, wirkt er sich nicht auf den zugrunde liegenden verwalteten Rückruf aus. er <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> wird daher verwendet, um einen Verweis auf den Delegaten hinzuzufügen, der die Verlagerung des Delegaten ermöglicht, aber die Beseitigung verhindert. Wenn Sie GCHandle anstelle von pin_ptr verwenden, wird das Fragmentierungs Potenzial des verwalteten Heaps reduziert.

```cpp
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example-function-pointer-stored-by-unmanaged-api"></a>Beispiel: Funktionszeiger, der von der nicht verwalteten API gespeichert wird

Das folgende Beispiel ähnelt dem vorherigen Beispiel, aber in diesem Fall wird der bereitgestellte Funktionszeiger von der nicht verwalteten API gespeichert, sodass er jederzeit aufgerufen werden kann, sodass Garbage Collection für eine beliebige Zeitspanne unterdrückt werden muss. Im folgenden Beispiel wird eine globale Instanz von verwendet, <xref:System.Runtime.InteropServices.GCHandle> um zu verhindern, dass der Delegat unabhängig vom Funktionsbereich verschoben wird. Wie im ersten Beispiel erläutert, ist die Verwendung von pin_ptr für diese Beispiele unnötig, aber in diesem Fall funktioniert nicht trotzdem, da der Bereich eines pin_ptr auf eine einzelne Funktion beschränkt ist.

```cpp
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
