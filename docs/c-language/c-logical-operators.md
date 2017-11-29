---
title: Logische C-Operatoren | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b97509fbbfdf0bb169af1dae61e07fa6f4ba31d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="c-logical-operators"></a>C-Operatoren (logisch)
Die logischen Operatoren führen logische AND (**&&**)- und logische OR ( `||` )-Operationen aus.  
  
 **Syntax**  
  
 *logical-AND-expression*:  
 *inclusive-OR-expression*  
  
 *logical-AND-expression*  **&&**  *inclusive-OR-expression*  
  
 *logical-OR-expression*:  
 *logical-AND-expression*  
  
 *logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*  
  
 Logische Operatoren führen nicht die üblichen arithmetischen Konvertierungen aus. Stattdessen werten sie jeden Operanden hinsichtlich seiner Übereinstimmung mit 0 (null) aus. Das Ergebnis einer logischen Operation ist entweder 0 (null) oder 1. Der Ergebnis ist vom Typ `int`.  
  
 Die logischen C-Operatoren sind im Folgenden beschrieben:  
  
|Operator|Beschreibung|  
|--------------|-----------------|  
|**&&**|Der logische AND-Operator gibt den Wert 1 an, wenn beide Operanden Werte ungleich 0 aufweisen. Wenn einer der beiden Operanden gleich 0 (null) ist, ist das Ergebnis 0 (null). Wenn der erste Operand einer logischen AND-Operation gleich 0 ist, wird der zweite Operand nicht ausgewertet.|  
|`&#124;&#124;`|Der logische OR-Operator führt eine inklusive OR-Operation für seinen Operanden aus. Das Ergebnis ist 0 (null), wenn beide Operanden den Wert 0 (null) aufweisen. Wenn einer der beiden Operanden einen Wert ungleich 0 (null) aufweist, ist das Ergebnis 1. Wenn der erste Operand einer logischen OR-Operation einen Wert ungleich 0 (null) aufweist, wird der zweite Operand nicht ausgewertet.|  
  
 Die Operanden logischer UND- und logischer OR-Ausdrücke werden von links nach rechts ausgewertet. Wenn der Wert des ersten Operanden ausreicht, um das Ergebnis der Operation zu bestimmen, wird der zweite Operand nicht ausgewertet. Dies wird als "Kurzschlussauswertung" bezeichnet. Es gibt einen Sequenzpunkt nach dem ersten Operanden. Weitere Informationen finden Sie unter [Sequenzpunkte](../c-language/c-sequence-points.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die logischen Operatoren veranschaulicht:  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 In diesem Beispiel wird die `printf`-Funktion aufgerufen, um eine Meldung auszugeben, wenn `x` kleiner ist als `y` und `y` kleiner als `z` ist. Wenn `x` größer ist als `y`, wird der zweite Operand (`y < z`) nicht ausgewertet und nichts wird ausgegeben. Beachten Sie, dass dies Probleme verursachen könnte, wenn der zweite Operand Nebeneffekte hat, auf die aus einem anderen Grund zugegriffen wird.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 In diesem Beispiel, wenn `x` entweder gleich `w`, `y` oder `z` ist, wird das zweite Argument für die `printf`-Funktion mit "true" ausgewertet, und der Wert 1 wird ausgegeben. Andernfalls wird dies mit "false" ausgewertet, und der Wert 0 (null) wird ausgegeben. Sobald eine der Bedingungen mit dem Ergebnis "true" ausgewertet wird, wird die Auswertung beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Logischer AND-Operator: &&](../cpp/logical-and-operator-amp-amp.md)   
 [Logischer OR-Operator: &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)