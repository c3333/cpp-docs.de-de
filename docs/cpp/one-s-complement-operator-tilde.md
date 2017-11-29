---
title: 'Eine &#39; s Komplementoperator: ~ | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs: C++
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb63adc5d776bec488661ea3e575c8693ea1b728
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="one39s-complement-operator-"></a>Eine &#39; s Komplementoperator: ~
## <a name="syntax"></a>Syntax  
  
```  
  
~ cast-expression  
```  
  
## <a name="remarks"></a>Hinweise  
 Der Einerkomplementoperator (`~`), der manchmal als "bitweiser Komplementoperator" bezeichnet wird, ergibt eine bitweise Einerkomplement seines Operanden. Das bedeutet, dass jedes Bit, das 1 im Operanden ist, 0 im Ergebnis ist. Umgekehrt ist jedes Bit, das 0 im Operanden ist, im Ergebnis 1. Der Operand für den Einerkomplementoperator muss ein ganzzahliger Typ sein.  
  
## <a name="operator-keyword-for-"></a>Operator-Schlüsselwort für ~  
 Der `compl`-Operator ist die Textentsprechung von `~`. Es gibt zwei Möglichkeiten, den Zugriff auf die `compl` -Operator in Programmen: Fügen Sie die Headerdatei `iso646.h`, oder Kompilieren Sie mit ["/ Za"](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 In diesem Beispiel ist der neue Wert, der `y` zugewiesen ist, das Einerkomplement des Werts ohne Vorzeichen 0xFFFF oder 0x0000.  
  
 Ganzzahlige Erweiterung wird für ganzzahlige Operanden durchgeführt, und der resultierende Typ ist der Typ, auf den der Operand erweitert wird. Finden Sie unter [Standardkonvertierungen](standard-conversions.md) für Weitere Informationen über die Durchführung der heraufstufung.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke mit Unäroperatoren](../cpp/expressions-with-unary-operators.md)   
 [Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md)