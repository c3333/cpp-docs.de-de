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
ms.openlocfilehash: 2f2471e36d7551cab9edb68d7babeb1419e8e20c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544952"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Gewusst wie: Objektverweis in nicht verwaltetem Arbeitsspeicher

Sie können gcroot. h verwenden, das <xref:System.Runtime.InteropServices.GCHandle>umschließt, um einen CLR-Objekt Verweis im nicht verwalteten Speicher zu speichern. Alternativ können Sie `GCHandle` direkt verwenden.

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

`GCHandle` bietet Ihnen die Möglichkeit, einen verwalteten Objekt Verweis in nicht verwaltetem Speicher zu speichern.  Verwenden Sie die <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>-Methode, um ein undurchsichtiges Handle für ein verwaltetes Objekt zu erstellen, und <xref:System.Runtime.InteropServices.GCHandle.Free%2A>, um es freizugeben. Außerdem können Sie mit der <xref:System.Runtime.InteropServices.GCHandle.Target%2A>-Methode den Objekt Verweis aus dem Handle in verwaltetem Code abrufen.

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

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
