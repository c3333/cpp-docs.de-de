---
title: Back_inserter-Funktion | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Windows::Foundation::Collections::back_inserter
dev_langs: C++
helpviewer_keywords: back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: eb2b4925ba1b0c6c9a8728b66c338ea50229d0f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="backinserter-function"></a>back_inserter-Funktion
Gibt einen Iterator zurück, der dazu verwendet wird, Elemente am Ende der angegebenen Auflistung einzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parameter  
 `T`  
 Ein Vorlagentyp-Parameter.  
  
 `v`  
 Ein Schnittstellenzeiger, der Zugriff auf die zugrunde liegende Auflistung bietet.  
  
### <a name="return-value"></a>Rückgabewert  
 Ein Iterator.  
  
### <a name="requirements"></a>Anforderungen  
 **Header:** collection.h  
  
 **Namespace:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Siehe auch  
 [Collections-Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)