---
title: 'hash_multimap:: const_reference (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::const_reference
dev_langs: C++
helpviewer_keywords: const_reference member [STL/CLR]
ms.assetid: c8e461bb-64cd-4868-a63e-77c197084431
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e34e289692a1f31b512a1fb8d810e773e6562f7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultimapconstreference-stlclr"></a>hash_multimap::const_reference (STL/CLR)
Der Typ eines konstanten Verweises auf ein Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef value_type% const_reference;  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Typ beschreibt einen konstanten Verweis auf ein Element.  
  
## <a name="example"></a>Beispiel  
  
```  
// cliext_hash_multimap_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_multimap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_multimap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<Cliext Hash_map/>  
  
 **Namespace:** Cliext  
  
## <a name="see-also"></a>Siehe auch  
 [hash_multimap-Element (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap:: Reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)   
 [hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)