---
title: Compilerwarnung (Stufe 4) C4220 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4220
dev_langs: C++
helpviewer_keywords: C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 82e921ecbb19ff705c7e2341d39d07991d6cb30a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4220"></a>Compilerwarnung (Stufe 4) C4220
Varargs entspricht der verbleibende Parameter  
  
 Unter den Standard-Microsoft-Erweiterungen (/ Ze) entspricht ein Zeiger auf eine Funktion einen Zeiger auf eine Funktion mit ähnliche, aber Variablen, Argumenten.  
  
## <a name="example"></a>Beispiel  
  
```  
// C4220.c  
// compile with: /W4  
  
int ( *pFunc1) ( int a, ... );  
int ( *pFunc2) ( int a, int b);  
  
int main()  
{  
   if ( pFunc1 != pFunc2 ) {};  // C4220  
}  
```  
  
 Derartige Zeiger stimmen nicht überein, ANSI-Kompatibilität (["/ Za"](../../build/reference/za-ze-disable-language-extensions.md)).