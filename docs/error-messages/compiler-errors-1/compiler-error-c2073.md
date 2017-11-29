---
title: Compiler-Fehler C2073 generiert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2073
dev_langs:
- C++
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 28f44a0a51e5b1ff1c6cb39e8a330c4ac0bd3154
ms.contentlocale: de-de
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2073"></a>Compiler-Fehler C2073 generiert
'Bezeichner': Elemente des teilweise initialisierte Arrays müssen über einen Standardkonstruktor verfügen  
  
 Für ein Array mit benutzerdefinierten Typen oder Konstanten wurden zu wenige Initialisierer angegeben. Wenn keine explizite Initialisierung und kein entsprechender Konstruktor für einen Arraymember nicht angegeben werden, muss ein Standardkonstruktor angegeben werden.  
  
 Im folgende Beispiel wird C2073 generiert:  
  
```  
// C2073.cpp  
class A {  
public:  
   A( int );   // constructor for ints only  
};  
A a[3] = { A(1), A(2) };   // C2073, no default constructor  
```  
  
```  
// C2073b.cpp  
// compile with: /c  
class B {  
public:  
   B();   // default constructor declared  
   B( int );  
};  
B b[3] = { B(1), B(2) };   // OK  
```