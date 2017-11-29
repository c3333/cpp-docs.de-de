---
title: Switch_type | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.switch_type
dev_langs: C++
helpviewer_keywords: switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99ec139c1ff10456639249c94451877a18cbbf51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="switchtype"></a>switch_type
Identifiziert den Typ der Variablen als die union Discriminant verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 Der Switchtyp kann eine ganze Zahl, Zeichen, Boolean oder eines Enumerationswerts Typ sein.  
  
## <a name="remarks"></a>Hinweise  
 Die **Switch_type** C++-Attribut hat die gleiche Funktionalität wie die [Switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL-Attribut.  
  
 C++-Attribute unterstützen keine [gekapselt Unions](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Nonencapsulated Unions](http://msdn.microsoft.com/library/windows/desktop/aa367119) werden nur in der folgenden Form unterstützt:  
  
```  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>Beispiel  
 Finden Sie unter der [Fall](../windows/case-cpp.md) Beispiel für ein Beispiel für die Verwendung von **Switch_type**.  
  
## <a name="requirements"></a>Anforderungen  
  
### <a name="attribute-context"></a>Attributkontext  
  
|||  
|-|-|  
|**Betrifft**|`typedef`|  
|**Wiederholbar**|Nein|  
|**Erforderliche Attribute**|Keine|  
|**Ungültige Attribute**|Keine|  
  
 Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDL-Attribute](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union- und Struct-Attribute](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   