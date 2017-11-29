---
title: Befehlszeilenwarnung D9026 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9026
dev_langs: C++
helpviewer_keywords: D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eead2bc96a24fd86b123ab4853bfc8ea01166804
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9026"></a>Befehlszeilenwarnung D9026
Optionen gelten für die gesamte Befehlszeile.  
  
 Nachdem ein Dateiname angegeben wurde, wurde eine Option für einen Befehl angegeben. Die Option wurde auf die Datei angewendet, das ihm vorausgeht.  
  
 Beispielsweise ist in den Befehl  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 die Datei VERDI.c wird mit der Option/G5 und nicht vom Standard/G4 kompiliert werden.  
  
 Dieses Verhalten unterscheidet sich von dem einiger früherer Versionen, die angewendet werden, nur die Optionen, die vor dem Dateinamen, wodurch VERDI.c angegeben, das kompiliert wird mit/G4 und wurden mithilfe von/G5 kompiliert wird.