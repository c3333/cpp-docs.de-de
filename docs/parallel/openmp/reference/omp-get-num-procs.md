---
title: Omp_get_num_procs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_get_num_procs
dev_langs: C++
helpviewer_keywords: omp_get_num_procs OpenMP function
ms.assetid: 14a10b8f-e59b-4211-a292-687648c9f760
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4a90da24d9c780ebd59d8e15272ac66615bbb323
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="ompgetnumprocs"></a>omp_get_num_procs
Gibt die Anzahl der Prozessoren, die verfügbar sind, wenn die Funktion aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
int omp_get_num_procs();  
```  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen finden Sie unter [3.1.5 Omp_get_num_procs-Funktion](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// omp_get_num_procs.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    printf_s("%d\n", omp_get_num_procs( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_num_procs( ));  
        }  
}  
```  
  
```Output  
// Expect the following output when the example is run on a two-processor machine:  
2  
2  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen](../../../parallel/openmp/reference/openmp-functions.md)