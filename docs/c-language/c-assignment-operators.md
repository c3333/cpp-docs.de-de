---
title: C-Zuweisungsoperatoren
description: Die standardmäßigen Zuweisungsoperatoren der Sprache C, ihre Syntax und Bedeutung.
ms.date: 10/30/2020
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
ms.openlocfilehash: 460e18772689de0d28fcfda3295a49b2f8a3c0d7
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238511"
---
# <a name="c-assignment-operators"></a>C-Zuweisungsoperatoren

Eine Zuweisungsvorgang weist den Wert des rechten Operanden dem Speicherort zu, der vom linken Operanden benannt wird. Deshalb muss der linke Operand eines Zuweisungsvorgangs ein änderbarer l-Wert sein. Nach der Zuweisung hat ein Zuweisungsausdruck den Wert des linken Operanden, ist jedoch kein L-Wert.

## <a name="syntax"></a>Syntax

*`assignment-expression`* :\
&emsp;*`conditional-expression`*\
&emsp;*`unary-expression`* *`assignment-operator`* *`assignment-expression`*

*`assignment-operator`* : eines der folgenden Zeichen<br/>
&emsp;**`=`** **`*=`** **`/=`** **`%=`** **`+=`** **`-=`** **`<<=`** **`>>=`** **`&=`** **`^=`** **`|=`**

Die Zuweisungsoperatoren in C können Werte in einem einzelnen Vorgang transformieren und zuweisen. C stellt die folgenden Zuweisungsoperatoren bereit:

|Operator|Vorgang ausgeführt|
|--------------|-------------------------|
|**`=`**|Einfache Zuweisung|
|**`*=`**|Multiplikationszuweisung|
|**`/=`**|Divisionszuweisung|
|**`%=`**|Restzuweisung|
|**`+=`**|Additionszuweisung|
|**`-=`**|Subtraktionszuweisung|
|**`<<=`**|Linksschiebezuweisung|
|**`>>=`**|Rechtsschiebezuweisung|
|**`&=`**|Bitweise AND-Zuweisung|
|**`^=`**|Bitweise exklusive OR-Zuweisung|
|**`|=`**|Bitweise inklusive OR-Zuweisung|

In der Zuweisung wird der Typ des rechten Werts in den Typ des linken Werts konvertiert, und der Wert wird im linken Operanden gespeichert, nachdem die Zuweisung stattgefunden hat. Der linke Operand darf kein Array, keine Funktion und keine Konstante sein. Der bestimmte Konvertierungspfad, der von den beiden Typen abhängt, wird ausführlich in [Typkonvertierungen](../c-language/type-conversions-c.md) erläutert.

## <a name="see-also"></a>Siehe auch

- [Zuweisungsoperatoren](../cpp/assignment-operators.md)
