---
title: is_nothrow_copy_constructible-Klasse | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_copy_constructible
dev_langs: C++
helpviewer_keywords: is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b1ce02c71fb7745465d21c7a4004ebc00ea7ddb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible-Klasse
Testet, ob der Typ einen **nothrow**-Kopierkonstruktor aufweist.  
  
## <a name="syntax"></a>Syntax  
  
```
template <class Ty>
struct is_nothrow_copy_constructible;
```  
  
#### <a name="parameters"></a>Parameter  
 `Ty`  
 Der abzufragende Typ.  
  
## <a name="remarks"></a>Hinweise  
 Eine Instanz des Typprädikats ist "true", wenn der `Ty`-Typ einen nothrow-Kopienkonstruktor aufweist; andernfalls "false".  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** \<type_traits>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Siehe auch  
 [<type_traits>](../standard-library/type-traits.md)




