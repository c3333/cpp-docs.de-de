---
title: MAKRO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MACRO
dev_langs: C++
helpviewer_keywords: MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0517357b204b1c4c90584d26d844639c9bc5169f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="macro"></a>MACRO
Markiert einen Makro-Block aufgerufen *Namen* und richtet *Parameter* Platzhalter für Argumente zu übergeben, wenn das Makro aufgerufen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
   name MACRO [[parameter [[:REQ | :=default | :VARARG]]]]...  
statements  
ENDM [[value]]  
```  
  
## <a name="remarks"></a>Hinweise  
 Eine Makrofunktion gibt *Wert* an die aufrufende Anweisung.  
  
## <a name="see-also"></a>Siehe auch  
 [Anweisungen – Referenz](../../assembler/masm/directives-reference.md)