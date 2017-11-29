---
title: auto_gcroot::Operator Auto_gcroot | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_gcroot.operator auto_gcroot
- auto_gcroot::operator auto_gcroot
- msclr.auto_gcroot.operator auto_gcroot
- msclr::auto_gcroot::operator auto_gcroot
dev_langs: C++
helpviewer_keywords: auto_gcroot operator
ms.assetid: 43e3f27a-9f68-444f-9149-a9282a9b935a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 339df92e4b5085dfcfbc1eea1025612106dad6e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="autogcrootoperator-autogcroot"></a>auto_gcroot::operator auto_gcroot
Typumwandlung Operator zwischen `auto_gcroot` und kompatible Typen.  
  
## <a name="syntax"></a>Syntax  
  
```  
template<typename _other_type>  
operator auto_gcroot<_other_type>();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die aktuelle `auto_gcroot` umgewandelt `auto_gcroot<_other_type>`.  
  
## <a name="example"></a>Beispiel  
  
```  
// msl_auto_gcroot_op_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:     
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {}  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:  
   ClassB( String ^ s) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main() {  
   auto_gcroot<ClassB^> b = gcnew ClassB("first");  
   b->PrintHello();  
   auto_gcroot<ClassA^> a = (auto_gcroot<ClassA^>)b;  
   a->PrintHello();  
}  
```  
  
```Output  
Hello from first B!  
Hello from first A!  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Headerdatei** \<msclr\auto_gcroot.h >  
  
 **Namespace** Msclr  
  
## <a name="see-also"></a>Siehe auch  
 [auto_gcroot-Members](../dotnet/auto-gcroot-members.md)