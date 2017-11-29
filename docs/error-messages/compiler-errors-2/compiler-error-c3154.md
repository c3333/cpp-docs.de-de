---
title: Compiler-Fehler C3154 generiert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3154
dev_langs: C++
helpviewer_keywords: C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de38898f775d621edfec464de8a51d20c3bdb4f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3154"></a>Compiler-Fehler C3154 generiert
Erwartet ',', bevor Sie mit den Auslassungspunkten. Nicht durch Trennzeichen getrennte Auslassungszeichen werden unter Parameter Array-Funktionen nicht unterstützt.  
  
 Eine Variablen argumentsfunktion wurde nicht ordnungsgemäß deklariert.  
  
 Weitere Informationen finden Sie unter [Variablenargumentlisten (...) (C + C++ / CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird C3154 generiert.  
  
```  
// C3154.cpp  
// compile with: /clr  
ref struct R {  
   void Func(int ... array<int> ^);   // C3154  
   void Func2(int i, ... array<int> ^){}   // OK  
   void Func3(array<int> ^){}   // OK  
   void Func4(... array<int> ^){}   // OK  
};  
  
int main() {  
   R ^ r = gcnew R;  
   r->Func4(1,2,3);  
}  
```