---
title: CElementTraits Klasse | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs: C++
helpviewer_keywords: CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cda18f6148f9a1cbc39a6e7003cce6324e36eeeb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="celementtraits-class"></a>CElementTraits-Klasse
Diese Klasse wird von Auflistungsklassen verschieben, kopieren, Vergleichsoperatoren und Hashvorgängen Methoden und Funktionen bereit.  
  
## <a name="syntax"></a>Syntax  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parameter  
 `T`  
 Der Typ der Daten in der Auflistung gespeichert werden.  
  
## <a name="remarks"></a>Hinweise  
 Diese Klasse bietet statische Standard-Funktionen und-Methoden für verschieben, kopieren, vergleichen und hashing ein Klassenobjekt Auflistung gespeicherten Elemente. `CElementTraits`wird als Standardanbieter dieser Vorgänge angegeben, indem die Auflistungsklassen [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), und [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Die standardimplementierungen für einfache Datentypen reicht aus, aber wenn die Auflistungsklassen verwendet werden, um komplexere Objekte zu speichern, die Funktionen und Methoden müssen überschrieben werden vom Benutzer bereitgestellte Implementierungen.  
  
 Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** atlcoll.h  
  
## <a name="see-also"></a>Siehe auch  
 [CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)   
 [Klassenübersicht](../../atl/atl-class-overview.md)