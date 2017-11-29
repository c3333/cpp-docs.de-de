---
title: Compiler-Fehler C2081 generiert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20f9f98ca03b9ed71d360b1b7c8bb64494a58416
ms.contentlocale: de-de
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2081"></a>Compiler-Fehler C2081 generiert
'Bezeichner': Name in der formalen Parameter ist ungültig  
  
 Der Bezeichner verursacht einen Syntaxfehler.  
  
 Dieser Fehler kann verursacht werden, mithilfe des alten Stils für die Liste der formalen Parameter. Sie müssen den Typ des formalen Parameter in der Liste der formalen Parameter angeben.  
  
 Im folgende Beispiel wird C2081 generiert:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 Mögliche Lösung:  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```