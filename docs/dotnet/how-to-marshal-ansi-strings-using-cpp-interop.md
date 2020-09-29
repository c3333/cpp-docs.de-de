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
ms.openlocfilehash: 3bdffa761bef74b9956842122b913e8213c736e9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414567"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Gewusst wie: Marshallen von ANSI-Zeichenfolgen mit C++-Interop

In diesem Thema wird veranschaulicht, wie ANSI-Zeichen folgen mit C++-Interop, aber der .NET Framework die Zeichen folgen <xref:System.String> im Unicode-Format darstellen, sodass die Konvertierung in ANSI einen zusätzlichen Schritt darstellt. Informationen zum interagieren mit anderen Zeichen folgen Typen finden Sie in den folgenden Themen:

- [Gewusst wie: Mars Hallen von Unicode-Zeichen folgen mit C++-Interop](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Gewusst wie: Mars Hallen von com-Zeichen folgen mit C++-Interop](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. diese Funktionen werden jedoch auf die gleiche Weise interagiert, wenn Sie in separaten Dateien definiert werden. Da Dateien, die nur nicht verwaltete Funktionen enthalten, nicht mit/CLR kompiliert werden müssen [(Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md), können Sie Ihre Leistungsmerkmale beibehalten.

## <a name="example-pass-ansi-string"></a>Beispiel: übergeben der ANSI-Zeichenfolge

Im Beispiel wird veranschaulicht, wie mithilfe von eine ANSI-Zeichenfolge von einer verwalteten an eine nicht verwaltete Funktion übergeben wird <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> . Diese Methode ordnet dem nicht verwalteten Heap Speicher zu und gibt die Adresse zurück, nachdem die Konvertierung durchgeführt wurde. Dies bedeutet, dass kein anheften notwendig ist (weil der Arbeitsspeicher auf dem GC-Heap nicht an die nicht verwaltete Funktion übergeben wird) und dass der von zurückgegebene IntPtr <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> explizit freigegeben werden muss oder dass ein Speicher abgebungs Ergebnis entsteht.

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

## <a name="example-data-marshaling-required-to-access-ansi-string"></a>Beispiel: für den Zugriff auf die ANSI-Zeichenfolge erforderliches Daten Marshalling

Das folgende Beispiel veranschaulicht das Daten Marshalling, das für den Zugriff auf eine ANSI-Zeichenfolge in einer verwalteten Funktion erforderlich ist, die von einer nicht verwalteten Funktion aufgerufen wird. Die verwaltete Funktion kann beim Empfang der systemeigenen Zeichenfolge Sie entweder direkt verwenden oder mithilfe der-Methode in eine verwaltete Zeichenfolge konvertieren <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> , wie gezeigt.

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

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
