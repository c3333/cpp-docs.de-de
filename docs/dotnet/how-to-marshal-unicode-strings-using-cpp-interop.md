---
title: 'Gewusst wie: Marshallen von Unicode-Zeichenfolgen mit C++-Interop'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f666e52b604e4713f02cb14744ac12a0407366a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544886"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Gewusst wie: Marshallen von Unicode-Zeichenfolgen mit C++-Interop

In diesem Thema wird ein Aspekt der C++ visuellen Interoperabilität veranschaulicht. Weitere Informationen finden Sie unter [using C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

In den folgenden Codebeispielen werden [verwaltete und nicht verwaltete #pragma-](../preprocessor/managed-unmanaged.md) Direktiven verwendet, um verwaltete und nicht verwaltete Funktionen in der gleichen Datei zu implementieren. diese Funktionen werden jedoch auf die gleiche Weise interagiert, wenn Sie in separaten Dateien definiert werden. Dateien, die nur nicht verwaltete Funktionen enthalten, müssen nicht mit/CLR kompiliert werden [(Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md).

In diesem Thema wird veranschaulicht, wie Unicode-Zeichen folgen von einer verwalteten an eine nicht verwaltete Funktion und umgekehrt übermittelt werden können. Informationen zum interagieren mit anderen Zeichen folgen Typen finden Sie in den folgenden Themen:

- [Vorgehensweise: Marshallen von ANSI-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von COM-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Beispiel

Um eine Unicode-Zeichenfolge von einer verwalteten an eine nicht verwaltete Funktion zu übergeben, kann die ptrdestringchars-Funktion (deklariert in "Vcclr. h") verwendet werden, um auf den Speicher zuzugreifen, in dem die verwaltete Zeichenfolge gespeichert ist. Da diese Adresse an eine native Funktion übermittelt wird, ist es wichtig, dass der Arbeitsspeicher mit [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) fixiert wird, um zu verhindern, dass die Zeichen folgen Daten verschoben werden, wenn eine Garbage Collection Cycle stattfindet, während die nicht verwaltete Funktion ausgeführt wird.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Daten Marshalling, das für den Zugriff auf eine Unicode-Zeichenfolge in einer verwalteten Funktion erforderlich ist, die von einer nicht verwalteten Funktion aufgerufen wird. Die verwaltete Funktion konvertiert beim Empfang der systemeigenen Unicode-Zeichenfolge Sie mithilfe der <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>-Methode in eine verwaltete Zeichenfolge.

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
