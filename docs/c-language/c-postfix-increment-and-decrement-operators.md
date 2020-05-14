---
title: C - Inkrementierungs- und Dekrementierungsoperatoren in Postfixnotation
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8c2e3ba50ce3e768b377a588cd3e82ad29df79ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325574"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>C - Inkrementierungs- und Dekrementierungsoperatoren in Postfixnotation

Operanden der Postfix-Inkrement- und Postfix-Dekrementoperatoren sind skalare Typen, die änderbare L-Werte sind.

## <a name="syntax"></a>Syntax

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-Ausdruck*  **--**

Das Ergebnis des Postfix-Inkrementoperators oder Postfix-Dekrementoperators ist der Wert des Operanden. Nachdem das Ergebnis erreicht ist, wird der Wert des Operanden (erhöht oder verringert). Der folgende Code veranschaulicht den Postfix-Inkrementoperator.

```
if( var++ > 0 )
    *p++ = *q++;
```

In diesem Beispiel wird die Variable `var` mit 0 verglichen und dann erhöht. Wenn `var` vor der Erhöhung positiv war, wird die nächste Anweisung ausgeführt. Zuerst wird der Wert des Objekts, auf das durch `q` gezeigt wird, dem Objekt zugewiesen, auf das durch `p` gezeigt wird. Anschließend werden `q` und `p` erhöht.

## <a name="see-also"></a>Siehe auch

[Inkrementierungs- und Dekrementierungsoperatoren in Postfixnotation: ++ und --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
