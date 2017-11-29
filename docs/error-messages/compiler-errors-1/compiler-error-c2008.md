---
title: Compilerfehler Fehler C2008 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2008
dev_langs: C++
helpviewer_keywords: C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fafc8567da4c9310a2ea96497f5764bbd1337137
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2008"></a>Compilerfehler Fehler C2008
"Zeichen": unerwartetes Zeichen in Makrodefinition  
  
 Das Zeichen wird unmittelbar nach dem Makronamen angezeigt. Um den Fehler zu beheben, muss ein Leerzeichen nach dem Makronamen vorhanden sein.  
  
 Im folgende Beispiel wird C2008 generiert:  
  
```  
// C2008.cpp  
#define TEST1"mytest1"    // C2008  
```  
  
 Mögliche Lösung:  
  
```  
// C2008b.cpp  
// compile with: /c  
#define TEST2 "mytest2"  
```