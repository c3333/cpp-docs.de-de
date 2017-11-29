---
title: 'List:: Iterator (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::iterator
dev_langs: C++
helpviewer_keywords: iterator member [STL/CLR]
ms.assetid: a62893c5-a53c-48ca-9f95-1eb3306b5ddf
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58f0283250a4f4c1923c4f569226f8a01a316472
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="listiterator-stlclr"></a>list::iterator (STL/CLR)
Der Typ eines Iterators für die gesteuerte Sequenz.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Typ beschreibt ein Objekt vom angegebenen Typ `T1` , die als ein random-Access-Iterator für die gesteuerte Sequenz fungieren kann.  
  
## <a name="example"></a>Beispiel  
  
```  
// cliext_list_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x b c  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<Cliext/List >  
  
 **Namespace:** Cliext  
  
## <a name="see-also"></a>Siehe auch  
 [Liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)