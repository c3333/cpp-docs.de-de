---
title: range_error-Klasse | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::range_error
dev_langs: C++
helpviewer_keywords: range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5eb96029c8a9c920f87c55d8cb513e5b90650a37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="rangeerror-class"></a>range_error-Klasse
Die Klasse fungiert als Basisklasse für alle Ausnahmen, die ausgelöst werden, um einen Bereichsfehler zu melden.  
  
## <a name="syntax"></a>Syntax  
  
```  
class range_error : public runtime_error {  
public:  
    explicit range_error(const string& message);

    explicit range_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Hinweise  
 Der von [Was](../standard-library/exception-class.md) zurückgegebene Wert ist eine Kopie von **Nachricht**`.`[Daten](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Beispiel  
  
```cpp  
// range_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
using namespace std;  
int main()  
{  
   try   
   {  
      throw range_error( "The range is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught: The range is in error!  
Type: class std::range_error  
*\  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Siehe auch  
 [runtime_error-Klasse](../standard-library/runtime-error-class.md)   
 [Thread Safety in the C++ Standard Library (Threadsicherheit in der C++-Standardbibliothek)](../standard-library/thread-safety-in-the-cpp-standard-library.md)
