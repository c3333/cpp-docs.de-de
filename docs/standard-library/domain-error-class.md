---
title: domain_error-Klasse | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::domain_error
dev_langs: C++
helpviewer_keywords: domain_error class
ms.assetid: a1d8245d-61c2-4d1e-973f-073bd5dd5fa3
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ad7e82db687b3fdf81e25285e4a75e32ac1cbbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2017
---
# <a name="domainerror-class"></a>domain_error-Klasse
Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Domänenfehler zu melden.  
  
## <a name="syntax"></a>Syntax  
  
```  
class domain_error : public logic_error {  
public:  
    explicit domain_error(const string& message);

    explicit domain_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Hinweise  
 Der von [Was](../standard-library/exception-class.md) zurückgegebene Wert ist eine Kopie von **Nachricht**`.`[Daten](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Beispiel  
  
```cpp  
// domain_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw domain_error( "Your domain is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid(e).name( ) << endl;  
   };  
}  
\* Output:   
Caught: Your domain is in error!  
Type: class std::domain_error  
*\  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Siehe auch  
 [logic_error-Klasse](../standard-library/logic-error-class.md)   
 [Threadsicherheit in der C++-Standardbibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
