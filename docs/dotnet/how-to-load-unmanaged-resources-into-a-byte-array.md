---
title: 'Gewusst wie: Laden von nicht verwalteten Ressourcen in ein Byte-Array'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- native resources, loading into Byte array
- unmanaged resources, loading into Byte array
- native resources
ms.assetid: cdada6cd-6d42-437a-a90f-44a0b18d6a93
ms.openlocfilehash: b2b98ff3c4bbd857e3f5d861c1e0e8e2bd2f357b
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685804"
---
# <a name="how-to-load-unmanaged-resources-into-a-byte-array"></a>Gewusst wie: Laden von nicht verwalteten Ressourcen in ein Byte-Array

In diesem Thema werden verschiedene Möglichkeiten zum Laden von nicht verwalteten Ressourcen in ein- <xref:System.Byte> Array erläutert.

## <a name="examples"></a>Beispiele

Wenn Sie die Größe ihrer nicht verwalteten Ressource kennen, können Sie ein CLR-Array vorab zuordnen und dann die Ressource mithilfe eines Zeigers auf den Array Block des CLR-Arrays in das Array laden.

```cpp
// load_unmanaged_resources_into_Byte_array.cpp
// compile with: /clr
using namespace System;
void unmanaged_func( unsigned char * p ) {
   for ( int i = 0; i < 10; i++ )
      p[ i ] = i;
}

public ref class A {
public:
   void func() {
      array<Byte> ^b = gcnew array<Byte>(10);
      pin_ptr<Byte> p =  &b[ 0 ];
      Byte * np = p;
      unmanaged_func( np );   // pass pointer to the block of CLR array.
      for ( int i = 0; i < 10; i++ )
         Console::Write( b[ i ] );
      Console::WriteLine();
   }
};

int main() {
   A^ g = gcnew A;
   g->func();
}
```

```Output
0123456789
```

In diesem Beispiel wird gezeigt, wie Daten aus einem nicht verwalteten Speicherblock in ein verwaltetes Array kopiert werden.

```cpp
// load_unmanaged_resources_into_Byte_array_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <string.h>
int main() {
   char buf[] = "Native String";
   int len = strlen(buf);
   array<Byte> ^byteArray = gcnew array<Byte>(len + 2);

   // convert any native pointer to IntPtr by doing C-Style cast
   Marshal::Copy( (IntPtr)buf, byteArray, 0, len );
}
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
