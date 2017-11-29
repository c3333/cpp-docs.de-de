---
title: 'Runtimeclassbaset:: Asiid-Methode | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs: C++
helpviewer_keywords: AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 796718c4533bf8730ca7a4c733e5809fb0fde880
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID-Methode
Unterstützt die WRL-Infrastruktur und ist nicht direkt aus Ihrem Code verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `T`  
 Ein Typ, die Schnittstellen-ID, die vom Parameter angegebenen implementiert `riid`.  
  
 `implements`  
 Eine Variable des Typs von Template-Parameter angegebenen `T`.  
  
 `riid`  
 Der Schnittstellen-ID abgerufen werden soll.  
  
 `ppvObject`  
 Wenn dieser Vorgang erfolgreich ist, wird ein Zeiger-auf-a-Zeiger auf die Schnittstelle vom-Parameter angegebenen `riid`.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Ruft einen Zeiger auf die angegebene Schnittstellen-ID.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Siehe auch  
 [RuntimeClassBaseT-Struktur](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details-Namespace](../windows/microsoft-wrl-details-namespace.md)