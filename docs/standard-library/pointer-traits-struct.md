---
title: pointer_traits-Struktur | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
dev_langs: C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d40f9149a9a03e4de40713ba9c7c0ce65f0edad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="pointertraits-struct"></a>pointer_traits-Struktur
Stellt Informationen bereit, die für ein Objekt der Vorlagenklasse `allocator_traits` erforderlich sind, um eine Zuweisung mit Zeigertyp `Ptr` zu beschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
template <class Ptr>
struct pointer_traits;
```  
  
## <a name="remarks"></a>Hinweise  
 Ptr kann ein unformatierter Zeiger vom Typ `Ty *` oder eine Klasse mit den folgenden Eigenschaften sein.  
```  
struct Ptr
   { // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj);
   // optional
   };  
```
### <a name="typedefs"></a>TypeDefs  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`typedef T2 difference_type`|Der Typ `T2` ist `Ptr::difference_type`, wenn dieser Typ vorhanden ist, andernfalls ist er `ptrdiff_t`. Wenn `Ptr` ein unformatierter Zeiger ist, ist der Typ `ptrdiff_t`.|  
|`typedef T1 element_type`|Der Typ `T1` ist `Ptr::element_type`, wenn dieser Typ vorhanden ist, andernfalls ist er `Ty`. Wenn `Ptr` ein unformatierter Zeiger ist, ist der Typ `Ty`.|  
|`typedef Ptr pointer`|Der Typ lautet `Ptr`.|  
  
### <a name="structs"></a>Strukturen  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`pointer_traits::rebind`|Versucht, den zugrunde liegenden Zeigertyp in einen angegebenen Typ zu konvertieren.|  
  
### <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[pointer_to](#pointer_to)|Konvertiert einen beliebigen Verweis auf ein Objekt der Klasse `Ptr`.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<memory>  
  
 **Namespace:** std  
  
##  <a name="pointer_to"></a> pointer_to  
 Statische Methode, die `Ptr::pointer_to(obj)` zurückgibt, wenn diese Funktion vorhanden ist. Andernfalls ist es nicht möglich einen beliebigen Verweis auf ein Objekt der Klasse `Ptr` zu konvertieren. Wenn `Ptr` ein unformatierter Zeiger ist, gibt diese Methode `addressof(obj)` zurück.  
  
```cpp  
static pointer pointer_to(element_type& obj);
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<memory>](../standard-library/memory.md)   
 [allocator_traits-Klasse](../standard-library/allocator-traits-class.md)
