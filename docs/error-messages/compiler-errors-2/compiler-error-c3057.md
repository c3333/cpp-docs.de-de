---
title: Compilerfehler C3057 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3057
dev_langs:
- C++
helpviewer_keywords:
- C3057
ms.assetid: b0b2ba88-9c74-4bec-bf60-8fc72eade34c
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 424c4dfb224b3d0778f80148aaac11e11c9ff440
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3057"></a>Compilerfehler C3057
'Symbol': Die dynamische Initialisierung von threadprivate-Symbolen wird derzeit nicht unterstützt.  
  
 Der initialisierte Wert eines Symbols, der in einer [threadprivate](../../parallel/openmp/reference/threadprivate.md) -Klausel verwendet wird, muss zum Zeitpunkt der Kompilierung bekannt sein.  
  
 Im folgenden Beispiel wird C3057 generiert:  
  
```  
// C3057.cpp  
// compile with: /openmp /c  
extern int f();  
int x, y = f();  
int a, b;  
#pragma omp threadprivate(x, y)   // C3057  
  
#pragma omp threadprivate(a, b)  
  
int main() {  
   // Delete the following 4 lines to resolve.  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
  
   #pragma omp parallel copyin(a, b)  
   {  
      a = b;  
   }  
}  
```  
  
 Im folgenden Beispiel wird C3057 generiert:  
  
```  
// C3057b.cpp  
// compile with: /openmp /c  
extern int Initialize();  
int main() {  
   #pragma omp parallel  
   {  
      static int var = Initialize();  
      #pragma omp threadprivate(var)   // C3057  
   }  
  
   // OK  
   #pragma omp parallel  
   {  
      static int var2;  
      static bool initialized2;  
      #pragma omp threadprivate(var2, initialized2)  
      if (!initialized2) {  
         var2 = Initialize();  
         initialized2 = true;  
      }  
   }  
}  
```