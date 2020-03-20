---
title: 'Gewusst wie: Marshallen von ANSI-Zeichenfolgen mit C++-Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 6987b23311354cfe6fd095e0e811d043e9b9692e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545252"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Gewusst wie: Marshallen von ANSI-Zeichenfolgen mit C++-Interop

In diesem Thema wird veranschaulicht, wie ANSI-Zeichen C++ folgen mithilfe von Interop übermittelt werden können, aber die .NET Framework <xref:System.String> die Zeichen folgen im Unicode-Format darstellt. die Konvertierung in ANSI ist ein zusätzlicher Schritt. Informationen zum interagieren mit anderen Zeichen folgen Typen finden Sie in den folgenden Themen:

- [Vorgehensweise: Marshallen von Unicode-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von COM-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. diese Funktionen werden jedoch auf die gleiche Weise interagiert, wenn Sie in separaten Dateien definiert werden. Da Dateien, die nur nicht verwaltete Funktionen enthalten, nicht mit/CLR kompiliert werden müssen [(Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md), können Sie Ihre Leistungsmerkmale beibehalten.

## <a name="example"></a>Beispiel

Im Beispiel wird veranschaulicht, wie eine ANSI-Zeichenfolge von einer verwalteten an eine nicht verwaltete Funktion mithilfe von <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>übergeben wird. Diese Methode ordnet dem nicht verwalteten Heap Speicher zu und gibt die Adresse zurück, nachdem die Konvertierung durchgeführt wurde. Dies bedeutet, dass kein anheften notwendig ist (weil der Arbeitsspeicher auf dem GC-Heap nicht an die nicht verwaltete Funktion übergeben wird) und dass der von <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> zurückgegebene IntPtr explizit freigegeben werden muss oder dass ein Speicher abgebungs Ergebnis entsteht.

```cpp
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Daten Marshalling, das für den Zugriff auf eine ANSI-Zeichenfolge in einer verwalteten Funktion erforderlich ist, die von einer nicht verwalteten Funktion aufgerufen wird. Die verwaltete Funktion kann beim Empfang der systemeigenen Zeichenfolge Sie entweder direkt verwenden oder mithilfe der <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>-Methode in eine verwaltete Zeichenfolge konvertieren, wie gezeigt.

```cpp
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
