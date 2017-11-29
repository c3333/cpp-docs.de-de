---
title: Compilerfehler C3458 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3458
dev_langs:
- C++
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: fc2d65f3be48f65469a4d4c7a5c165fc3331d4c0
ms.contentlocale: de-de
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3458"></a>Compilerfehler C3458
'attribut1': Das Attribut 'attribut2' wurde bereits für 'konstrukt' angegeben  
  
 Zwei Attribute, die sich gegenseitig ausschließen, wurden für dasselbe Konstrukt angegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird C3458 generiert:  
  
```  
// C3458.cpp  
// compile with: /clr /c  
[System::Reflection::DefaultMember("Chars")]  
public ref class MyString {  
public:  
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458  
   property char default[int] {  
      char get(int index);  
      void set(int index, char c);  
   }  
};  
```