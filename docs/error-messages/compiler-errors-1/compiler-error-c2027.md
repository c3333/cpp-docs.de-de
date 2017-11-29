---
title: Compilerfehler Fehler C2027 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2a2fec9194858127ca08ecc0a891a81a91de48fa
ms.contentlocale: de-de
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2027"></a>Compilerfehler Fehler C2027
Verwenden eines undefinierten Typs 'Typ'  
  
 Ein Typ kann nicht verwendet werden, bis er definiert ist. Um den Fehler zu beheben, achten Sie darauf, dass der Typ vollständig definiert ist, bevor auf Sie verwiesen wird.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird C2027 generiert.  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>Beispiel  
 Es ist möglich, deklarieren Sie einen Zeiger auf einen Typ deklariert, aber nicht definiert.  Visual C++, nicht jedoch einen Verweis auf einen undefinierten Typ.  
  
 Im folgende Beispiel wird C2027 generiert.  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```