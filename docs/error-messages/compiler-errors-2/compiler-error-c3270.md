---
title: Compilerfehler C3270 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3270
dev_langs:
- C++
helpviewer_keywords:
- C3270
ms.assetid: 70e6e76b-7415-48f5-a61e-2ed50caf08e4
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 326f53f06c6cc4d93eb85f265df161c7b2b86535
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3270"></a>Compilerfehler C3270
"Feld": Das FieldOffset-Attribut ist im Kontext von "StructLayout(Explicit)" erforderlich und kann nur in diesem Kontext verwendet werden  
  
Ein Feld wurde mit markiert **FieldOffset**, das ist nur zulässig, wenn **StructLayout(Explicit)"** ist aktiviert.  
  
Im folgenden Beispiel wird C3270 generiert:  
  
```  
// C3270_2.cpp  
// compile with: /clr /c  
using namespace System::Runtime::InteropServices;  
  
[ StructLayout(LayoutKind::Sequential) ]  
// try the following line instead  
// [ StructLayout(LayoutKind::Explicit) ]  
public value struct MYUNION  
{  
   [FieldOffset(0)] int a;   // C3270  
   // ...  
};  
```  
