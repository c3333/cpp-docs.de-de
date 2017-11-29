---
title: Compilerfehler C2802 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2802
dev_langs: C++
helpviewer_keywords: C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: adc1b4178caebe9893727aaf8ff802d6f030e986
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2802"></a>Compilerfehler C2802
statische Member-'Operator Operator' hat keine formalen Parameter  
  
 Ein Operator deklariert, indem eine `static` Memberfunktion muss mindestens einen Parameter verfügen.  
  
 Im folgende Beispiel wird C2802 generiert:  
  
```  
// C2802.cpp  
// compile with: /clr /c  
ref class A {  
   static operator+ ();   // C2802  
   static operator+ (A^, A^);   // OK  
};  
```