---
title: Compiler-Fehler C2650 generiert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2650
dev_langs: C++
helpviewer_keywords: C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3352820434c8d794d4980a606cb945bd8ecc4a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2650"></a>Compiler-Fehler C2650 generiert
'Operator': eine virtuelle Funktion ist nicht möglich  
  
 Ein `new` oder `delete` Operator deklariert ist `virtual`. Diese Operatoren sind `static` Memberfunktionen dar und nicht mit `virtual`.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird C2650 generiert:  
  
```  
// C2650.cpp  
// compile with: /c  
class A {  
   virtual void* operator new( unsigned int );   // C2650  
   // try the following line instead  
   // void* operator new( unsigned int );  
};  
```