---
title: __invlpg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs: C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 735db37631fd0ddbc0918edb95230600275c6b4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="invlpg"></a>__invlpg
**Microsoft-spezifisch**  
  
 Generiert die X86 `invlpg` -Anweisung, die für die Seite zugeordnete Speicher verweist, zu den Übersetzung Lookaside-Puffer (TLB) erklärt `Address`.  
  
## <a name="syntax"></a>Syntax  
  
```  
void __invlpg(  
   void* Address  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in]`Address`  
 Eine 64-Bit-Adresse.  
  
## <a name="requirements"></a>Anforderungen  
  
|Systemintern|Architektur|  
|---------------|------------------|  
|`__invlpg`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Headerdatei** \<intrin.h >  
  
## <a name="remarks"></a>Hinweise  
 Die systeminterne Funktion `__invlpg` eine privilegierte Anweisung ausgibt, und ist nur verfügbar im Kernel-Modus mit einer Berechtigungsstufe (Systemsteuerungsoption) 0.  
  
 Diese Routine ist nur als systeminterne Funktion verfügbar.  
  
**Ende Microsoft-spezifisch**  
  
## <a name="see-also"></a>Siehe auch  
 [Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)