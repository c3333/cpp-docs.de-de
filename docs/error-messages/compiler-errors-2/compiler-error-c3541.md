---
title: Compilerfehler C3541 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3541
dev_langs: C++
helpviewer_keywords: C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 78b4c228999560807aa28dbaecfaa8f0af7b379a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3541"></a>Compilerfehler C3541
"Typ": Typeid kann nicht angewendet werden, um ein Typ, der "auto" enthält  
  
 Die [Typeid](../../windows/typeid-cpp-component-extensions.md) Operator kann nicht auf den angegebenen Typ angewendet werden, da sie enthält die `auto` Spezifizierer.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel ergibt C3541.  
  
```  
// C3541.cpp  
// Compile with /Zc:auto  
#include <typeinfo>  
int main() {  
    auto x = 123;  
    typeid(x);    // OK  
    typeid(auto); // C3541  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Auto-Schlüsselwort](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (Variablentyp ableiten)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [typeid](../../windows/typeid-cpp-component-extensions.md)