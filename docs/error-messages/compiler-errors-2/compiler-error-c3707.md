---
title: Compilerfehler C3707 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3707
dev_langs: C++
helpviewer_keywords: C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7167ea0df9bc0846de16be40d722c63bfea11c32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3707"></a>Compilerfehler C3707
'Funktion': Dispinterface-Methode muss eine Dispid haben  
  
 Bei Verwendung einer `dispinterface` -Methode, müssen Sie sie Zuweisen einer `dispid`. Um diesen Fehler zu beheben, weisen eine `dispid` auf die `dispinterface` Methode, z. B. durch die auskommentierung der `id` Attribut in der Methode im folgenden Beispiel. Weitere Informationen finden Sie unter den Attributen [Dispinterface](../../windows/dispinterface.md) und [Id](../../windows/id.md).  
  
 Im folgende Beispiel wird C3707 generiert:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```