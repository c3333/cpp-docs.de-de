---
title: Compilerfehler C3003 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3003
dev_langs:
- C++
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 98479fda012d06b9eff57b5fcbf4dc883c94d9e5
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3003"></a>Compilerfehler C3003
'Direktive': Nach Direktivenklauseln ist kein OpenMP-Direktivenname zulässig.  
  
 Ein OpenMP-Direktivenname darf nicht auf eine OpenMP-Direktivenklausel folgen.  
  
 Im folgenden Beispiel wird C3003 generiert:  
  
```  
// C3003.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
   #pragma omp parallel shared(x, y, z) for   // C3003  
}  
```