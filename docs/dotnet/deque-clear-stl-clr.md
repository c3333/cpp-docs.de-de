---
title: 'deque:: Clear (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::clear
dev_langs: C++
helpviewer_keywords: clear member [STL/CLR]
ms.assetid: 1d9a3d11-b3fa-43a7-a508-7a05cbcd91bf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5bb9f4c00976ce60901148509d9390b85412ab7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="dequeclear-stlclr"></a>deque::clear (STL/CLR)
Entfernt alle Elemente.  
  
## <a name="syntax"></a>Syntax  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Memberfunktion ruft tatsächlich [deque:: Erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md) `(` [deque:: begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md) `(),` [deque:: End (STL/CLR)](../dotnet/deque-end-stl-clr.md) `())`. Sie verwenden es, um sicherzustellen, dass die kontrollierte Sequenz leer ist.  
  
## <a name="example"></a>Beispiel  
  
```  
// cliext_deque_clear.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<Cliext/doppelschlange >  
  
 **Namespace:** Cliext  
  
## <a name="see-also"></a>Siehe auch  
 [Deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)