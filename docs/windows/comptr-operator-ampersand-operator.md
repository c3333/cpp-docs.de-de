---
title: Comptr::&amp; Operator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator&
dev_langs: C++
helpviewer_keywords: operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b464a77fedf0d996210040b744faea0ee7372ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperatoramp-operator"></a>Comptr::&amp; Operator
Gibt die Schnittstelle frei zugeordnete `ComPtr` -Objekt und ruft dann die Adresse der `ComPtr` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Einen schwachen Verweis auf das aktuelle `ComPtr`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode unterscheidet sich von [comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) , da diese Methode einen Verweis auf den Schnittstellenzeiger frei. Verwendung `ComPtr::GetAddressOf` Wenn Sie muss die Adresse des Schnittstellenzeigers, jedoch nicht diese Schnittstelle freigeben möchten.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Siehe auch  
 [ComPtr-Klasse](../windows/comptr-class.md)