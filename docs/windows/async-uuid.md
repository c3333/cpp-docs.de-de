---
title: Async_uuid | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.async_uuid
dev_langs: C++
helpviewer_keywords: async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b35791f67b712139210f383a0f9ef605efbacd0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="asyncuuid"></a>async_uuid
Gibt an, die synchrone und asynchrone Versionen einer COM-Schnittstelle definiert die MIDL-Compiler anweist, UUID.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      [async_uuid (  
   uuid  
)]  
```  
  
#### <a name="parameters"></a>Parameter  
 *UUID*  
 Die Version der Schnittstelle identifiziert UUID.  
  
## <a name="remarks"></a>Hinweise  
 Die **Async_uuid** C++-Attribut hat die gleiche Funktionalität wie die [Async_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL-Attribut.  
  
## <a name="example"></a>Beispiel  
  
```  
// cpp_attr_ref_async_uuid.cpp  
// compile with: /LD  
#include <Windows.h>  
[module(name="Test")];  
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),   
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
```  
  
## <a name="requirements"></a>Anforderungen  
  
### <a name="attribute-context"></a>Attributkontext  
  
|||  
|-|-|  
|**Betrifft**|`interface`|  
|**Wiederholbar**|Nein|  
|**Erforderliche Attribute**|Keine|  
|**Ungültige Attribute**|**Duale**, **Disp-Schnittstelle**|  
  
 Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDL-Attribute](../windows/idl-attributes.md)   
 [Schnittstellenattribut](../windows/interface-attributes.md)   