---
title: 'Gewusst wie: Objektverweis in nicht verwaltetem Arbeitsspeicher'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 13d5bd37a0f5e0b065aecb8c5b264fb70685363f
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684507"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Gewusst wie: Objektverweis in nicht verwaltetem Arbeitsspeicher

Sie können gcroot. h, das umschließt <xref:System.Runtime.InteropServices.GCHandle> , verwenden, um einen CLR-Objekt Verweis im nicht verwalteten Speicher zu speichern. Alternativ können Sie direkt verwenden `GCHandle` .

## <a name="examples"></a>Beispiele

```cpp
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

`GCHandle` bietet Ihnen die Möglichkeit, einen verwalteten Objekt Verweis in nicht verwaltetem Speicher zu speichern.  Verwenden Sie die <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> -Methode, um ein nicht transparentes Handle für ein verwaltetes Objekt zu erstellen und <xref:System.Runtime.InteropServices.GCHandle.Free%2A> es freizugeben. Außerdem können Sie mit der- <xref:System.Runtime.InteropServices.GCHandle.Target%2A> Methode den Objekt Verweis aus dem Handle in verwaltetem Code abrufen.

```cpp
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
