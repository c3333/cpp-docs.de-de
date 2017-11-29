---
title: Degradierung von Ganzzahlen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e09a81ca21f6e00777322178dcdf1c09ef22dd5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="demotion-of-integers"></a>Degradierung von Ganzzahlen
**ANSI 3.2.1.2** Das Ergebnis der Konvertierung einer ganzen Zahl in eine kürzere Ganzzahl mit Vorzeichen oder das Ergebnis der Konvertierung einer Ganzzahl ohne Vorzeichen in eine Ganzzahl mit Vorzeichen derselben Länge, wenn der Wert nicht dargestellt werden kann  
  
 Wenn eine ganze Zahl vom Typ **long** in den Typ **short** oder vom Typ **short** in den Typ `char` umgewandelt wird, werden die unwichtigsten Bytes beibehalten.  
  
 Diese Zeile weist beispielsweise  
  
```  
short x = (short)0x12345678L;  
```  
  
 `x` den Wert 0x5678 zu, und diese Zeile  
  
```  
char y = (char)0x1234;  
```  
  
 weist `y` den Wert 0x34 zu.  
  
 Wenn Variablen mit Vorzeichen in Variablen ohne Vorzeichen und umgekehrt konvertiert werden, bleiben die Bitmuster identisch. Zum Beispiel ergibt die Umwandlung von -2 (0xFE) in einen Wert ohne Vorzeichen 254 (auch 0xFE).  
  
## <a name="see-also"></a>Siehe auch  
 [Ganze Zahlen](../c-language/integers.md)