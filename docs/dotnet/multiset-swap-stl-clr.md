---
title: "multiset::swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap-Member [STL/CLR]"
ms.assetid: 8a3023c7-e58b-4ffe-8fd5-2e0bf02cc291
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# multiset::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Vertauscht den Inhalt von zwei Containern.  
  
## Syntax  
  
```  
void swap(multiset<Key>% right);  
```  
  
#### Parameter  
 right  
 Container, mit denen Inhalt getauscht werden soll.  
  
## Hinweise  
 Die Memberfunktion tauscht die gesteuerten Sequenzen zwischen `this` und `right` aus.  Sie geschieht bei der konstanten Zeit und es löst keine Ausnahmen aus.  Sie verwenden sie als schnelle Möglichkeit, der Inhalt zweier Containern auszutauschen.  
  
## Beispiel  
  
```  
// cliext_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymultiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **ein b c**  
 **d E\-F**  
 **d E\-F**  
 **ein b c**   
## Anforderungen  
 **Header:** \<cliext\/Satz\>  
  
 **Namespace:** cliext  
  
## Siehe auch  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::operator\=](../dotnet/multiset-operator-assign-stl-clr.md)