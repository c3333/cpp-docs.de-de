---
title: Compiler-Fehler C2748 generiert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2748
dev_langs: C++
helpviewer_keywords: C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0eaee593630a40a6bffb126e9eab8ed17668e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2748"></a>Compiler-Fehler C2748 generiert
verwaltet oder WinRT-Arrayerstellung muss eine Arraygröße oder einen Arrayinitialisierung besitzen  
  
 Eine verwaltete oder ein WinRT-Array wurde nicht ordnungsgemäß formatiert. Weitere Informationen finden Sie unter [Array](../../windows/arrays-cpp-component-extensions.md).  
  
 Im folgenden Beispiel wird C2748 generiert und gezeigt, wie Sie diesen Fehler beheben:  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```