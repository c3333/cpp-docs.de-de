---
title: Operator&lt;= (Deque) (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::operator<=
dev_langs: C++
helpviewer_keywords: operator<= member [STL/CLR]
ms.assetid: b70cc499-35fb-4fa5-b8e3-5270bc647ace
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a07a856abad67d13764b076b698f75dec40bd4c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="operatorlt-deque-stlclr"></a>Operator&lt;= (Deque) (STL/CLR)
Deque kleiner oder gleich Vergleich.  
  
## <a name="syntax"></a>Syntax  
  
```  
template<typename Value>  
    bool operator<=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>Parameter  
 links  
 Linker zu vergleichender Container.  
  
 Rechts  
 Rechter zu vergleichender Container.  
  
## <a name="remarks"></a>Hinweise  
 Gibt die Operatorfunktion `!(right < left)`. Sie zum Testen verwenden, ob `left` ist nicht geordnet nach `right` Wenn den zwei deque-Objekten aus verglichenen elementweise sind.  
  
## <a name="example"></a>Beispiel  
  
```  
// cliext_deque_operator_le.cpp   
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
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<Cliext/doppelschlange >  
  
 **Namespace:** Cliext  
  
## <a name="see-also"></a>Siehe auch  
 [Deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [Operator == (Deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)   
 [deque:: Operator! = (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)   
 [Operator\< (Deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [Operator > = (Deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)