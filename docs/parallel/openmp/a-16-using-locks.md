---
title: Verwendung von Sperren A.16 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 870895dae8aa6fe4b3720b9319359672fcb576af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="a16---using-locks"></a>A. 16   Verwenden von Sperren
Im folgenden Beispiel (für [Abschnitt 3.2](../../parallel/openmp/3-2-lock-functions.md) auf Seite 41) Beachten Sie, dass das Argument für die Lock-Funktionen Typ aufweisen soll `omp_lock_t`, und dass keine Notwendigkeit zum geleert besteht.  Die Lock-Funktionen dazu führen, dass die Threads im Leerlauf befindlich beim Eintritt in den ersten kritischen Abschnitt warten, jedoch andere Aufgaben während des Wartens auf dem zweiten Eintrag.  Die `omp_set_lock` Funktion blockiert, aber die `omp_test_lock` Funktion nicht der Fall, können die Arbeit in skip() durchgeführt werden.  
  
## <a name="example"></a>Beispiel  
  
### <a name="code"></a>Code  
  
```  
// omp_using_locks.c  
// compile with: /openmp /c  
#include <stdio.h>  
#include <omp.h>  
  
void work(int);  
void skip(int);  
  
int main() {  
   omp_lock_t lck;  
   int id;  
  
   omp_init_lock(&lck);  
   #pragma omp parallel shared(lck) private(id)  
   {  
      id = omp_get_thread_num();  
  
      omp_set_lock(&lck);  
      printf_s("My thread id is %d.\n", id);  
  
      // only one thread at a time can execute this printf  
      omp_unset_lock(&lck);  
  
      while (! omp_test_lock(&lck)) {  
         skip(id);   // we do not yet have the lock,  
                     // so we must do something else   
      }  
      work(id);     // we now have the lock  
                    // and can do the work   
      omp_unset_lock(&lck);  
   }  
   omp_destroy_lock(&lck);  
}  
```