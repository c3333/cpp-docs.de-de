---
title: C-Zuweisungsoperatoren
ms.date: 06/14/2018
helpviewer_keywords:
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
ms.openlocfilehash: e8ada96daaec249a05882aceae9b7d9e86b92065
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168798"
---
# <a name="c-assignment-operators"></a>C-Zuweisungsoperatoren

Eine Zuweisungsvorgang weist den Wert des rechten Operanden dem Speicherort zu, der vom linken Operanden benannt wird. Deshalb muss der linke Operand eines Zuweisungsvorgangs ein änderbarer l-Wert sein. Nach der Zuweisung hat ein Zuweisungsausdruck den Wert des linken Operanden, ist jedoch kein L-Wert.

## <a name="syntax"></a>Syntax

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Zuweisungs Operator* - *Zuweisungs* Operator ( *unärer Ausdruck* )

*assignment-operator*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **\*=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **|=**

Die Zuweisungsoperatoren in C können Werte in einem einzelnen Vorgang transformieren und zuweisen. C stellt die folgenden Zuweisungsoperatoren bereit:

|Operator|Vorgang ausgeführt|
|--------------|-------------------------|
|**=**|Einfache Zuweisung|
|**&#42;=**|Multiplikationszuweisung|
|**/=**|Divisionszuweisung|
|**%=**|Restzuweisung|
|**+=**|Additionszuweisung|
|**-=**|Subtraktionszuweisung|
|**<\<=**|Linksschiebezuweisung|
|**>>=**|Rechtsschiebezuweisung|
|**&=**|Bitweise AND-Zuweisung|
|**^=**|Bitweise exklusive OR-Zuweisung|
|**&#124;=**|Bitweise inklusive OR-Zuweisung|

In der Zuweisung wird der Typ des rechten Werts in den Typ des linken Werts konvertiert, und der Wert wird im linken Operanden gespeichert, nachdem die Zuweisung stattgefunden hat. Der linke Operand darf kein Array, keine Funktion und keine Konstante sein. Der bestimmte Konvertierungspfad, der von den beiden Typen abhängt, wird ausführlich in [Typkonvertierungen](../c-language/type-conversions-c.md) erläutert.

## <a name="see-also"></a>Weitere Informationen

- [Assignment Operators (Zuweisungsoperatoren)](../cpp/assignment-operators.md)
