---
title: Compilerfehler C2810 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2810
dev_langs:
- C++
helpviewer_keywords:
- C2810
ms.assetid: f63e8f24-d7f6-42ac-904f-72ff49592ba6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 80fdc399c5825b9bd625604e7f4366f98b9ee971
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2810"></a>Compilerfehler C2810
'Schnittstelle': eine Schnittstelle kann nur von einer anderen Schnittstelle erben  
  
 Ein [Schnittstelle](../../cpp/interface.md) kann nur von einer anderen Schnittstelle erben, und nicht von einer Klasse oder Struktur erben.  
  
 Im folgende Beispiel wird C2810 generiert:  
  
```  
// C2810.cpp  
#include <unknwn.h>  
class CBase1 {  
public:  
  HRESULT mf1();  
  int  m_i;  
};  
  
[object, uuid="40719E20-EF37-11D1-978D-0000F805D73B"]  
__interface IDerived : public CBase1 {  // C2810  
// try the following line instead  
// __interface IDerived {  
   HRESULT mf2(void *a);  
};  
  
struct CBase2 {  
   HRESULT mf1(int a, char *b);  
   HRESULT mf2();  
};  
```