---
title: Compilerfehler C3029 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3029
dev_langs:
- C++
helpviewer_keywords:
- C3029
ms.assetid: 655eb04d-504a-468d-8c0c-bda1e5f297b7
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b04e6004f02a57023ed999f30ec5f318e7a72bb4
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3029"></a>Compilerfehler C3029
"Symbol": Kann nur einmal in Datenfreigabeklauseln in einer OpenMP-Direktive vorkommen.  
  
 Ein Symbol wurde in mindestens einer Klausel in einer Direktive mehr als einmal verwendet. Das Symbol kann in der Direktive nur einmal verwendet werden.  
  
 Im folgenden Beispiel wird C3029 generiert:  
  
```  
// C3029.cpp  
// compile with: /openmp /link vcomps.lib  
#include "omp.h"  
  
int g_i;  
  
int main() {  
   int i, x;  
  
   #pragma omp parallel reduction(+ : x, x)   // C3029  
      ;  
  
   #pragma omp parallel reduction(+ : x)   // OK  
      ;  
  
   #pragma omp parallel private(x) reduction(+ : x)   // C3029  
      ;  
  
   #pragma omp parallel reduction(+ : x)   // OK  
      ;  
}  
```