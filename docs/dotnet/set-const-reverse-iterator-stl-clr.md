---
title: "set::const_reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator-Member [STL/CLR]"
ms.assetid: 60171be5-c4a8-4fce-89a9-6642d805bb57
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::const_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Der Typ eines konstanten umgekehrten Iterators für die gesteuerte Sequenz.  
  
## Syntax  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## Hinweise  
 Der Typ beschreibt ein Objekt des angegebenen Typs nicht `T4`, das als konstanter umgekehrter Iterator für die gesteuerte Sequenz dienen kann.  
  
## Beispiel  
  
```  
// cliext_set_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c a b**   
## Anforderungen  
 **Header:** \<cliext\/Satz\>  
  
 **Namespace:** cliext  
  
## Siehe auch  
 [set](../dotnet/set-stl-clr.md)   
 [set::reverse\_iterator](../dotnet/set-reverse-iterator-stl-clr.md)