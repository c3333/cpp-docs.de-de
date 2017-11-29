---
title: IsBaseOfStrict-Struktur | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs: C++
helpviewer_keywords: IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fd3d232094ed9a56db9cd0e14776ca0ec9eca8c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict-Struktur
Unterstützt die WRL-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### <a name="parameters"></a>Parameter  
 `Base`  
 Der Basistyp.  
  
 `Derived`  
 Der abgeleitete Typ.  
  
## <a name="remarks"></a>Hinweise  
 Testet, ob ein Typ die Basis eines anderen ist.  
  
 Die erste Vorlage testet, ob ein Typ von einem Basistyp abgeleitet ist ergeben **"true"** oder **"false"**. Die zweite Vorlage testet, ob ein Typ von sich selbst zu abgeleitet ist, ergibt immer **"false"**.  
  
## <a name="members"></a>Member  
  
### <a name="public-constants"></a>Öffentliche Konstanten  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IsBaseOfStrict::value-Konstante](../windows/isbaseofstrict-value-constant.md)|Gibt an, ob ein Typ die Basis eines anderen ist.|  
  
## <a name="inheritance-hierarchy"></a>Vererbungshierarchie  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** internal.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft::WRL::Details-Namespace](../windows/microsoft-wrl-details-namespace.md)