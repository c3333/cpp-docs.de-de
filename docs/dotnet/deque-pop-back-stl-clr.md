---
title: 'deque:: pop_back (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::pop_back
dev_langs: C++
helpviewer_keywords: pop_back member [STL/CLR]
ms.assetid: 528d2c89-104c-45f7-8f05-41fe217ee37c
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7c77183cba08ec1b01659192b130edcf28d2b1c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="dequepopback-stlclr"></a>deque::pop_back (STL/CLR)
Entfernt das letzte Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
void pop_back();  
```  
  
## <a name="remarks"></a>Hinweise  
 Die Memberfunktion entfernt das letzte Element der gesteuerten Sequenz, die nicht leer sein darf. Sie verwenden es, um durch ein Element auf der Rückseite die doppelschlange zu verkürzen.  
  
## <a name="example"></a>Beispiel  
  
```  
// cliext_deque_pop_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<Cliext/doppelschlange >  
  
 **Namespace:** Cliext  
  
## <a name="see-also"></a>Siehe auch  
 [Deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)   
 [deque:: push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)   
 [deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)