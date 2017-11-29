---
title: 'Vorgehensweise: Objektverweis in nicht verwalteten Speicher | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2d4f5a54d71a49d76b1fbc2ba31a0ffe42738b92
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Gewusst wie: Objektverweis in nicht verwaltetem Arbeitsspeicher
Sie können gcroot.h verwenden, das umschließt <xref:System.Runtime.InteropServices.GCHandle>zur Aufnahme eines CLR-Objektverweis in nicht verwalteten Speicher. Alternativ können Sie `GCHandle` direkt.  
  
## <a name="example"></a>Beispiel  
  
```  
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
 `GCHandle`bietet Ihnen eine Möglichkeit zum Verweis auf ein verwaltetes Objekt im nicht verwalteten Speicher zu behalten.  Verwenden Sie die <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> Methode, um ein nicht transparentes Handle zu einem verwalteten Objekt zu erstellen und <xref:System.Runtime.InteropServices.GCHandle.Free%2A> , diese freizugeben. Darüber hinaus die <xref:System.Runtime.InteropServices.GCHandle.Target%2A> Methode können Sie den Objektverweis wieder aus dem Handle in verwaltetem Code zu erhalten.  
  
```  
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