---
title: Compilerfehler C2890 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2890
dev_langs: C++
helpviewer_keywords: C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee25c25fd1c808ece4a6ef7f8538b83216c4b180
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2890"></a>Compilerfehler C2890
'Klasse': eine Verweisklasse kann nur eine Basisklasse für nicht-Schnittstelle haben  
  
 Eine Verweisklasse kann nur eine Basisklasse verfügen.  
  
 Im folgende Beispiel wird C2890 generiert:  
  
```  
// C2890.cpp  
// compile with: /clr /c  
ref class A {};  
ref class B {};  
ref class C : public A, public B {};   // C2890  
ref class D : public A {};   // OK  
```  