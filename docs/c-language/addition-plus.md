---
title: Addition (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 48672315960e32cb324aacc6c90d3d67891f3d39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313661"
---
# <a name="addition-"></a>Addition (+)

Der Additionsoperator ( **+** ) sorgt dafür, dass seine beiden Operanden hinzugefügt werden. Beide Operanden können entweder vom Typ „Ganze Zahl“ oder „Gleitkommazahl“ sein, oder ein Operand kann ein Zeiger und der andere eine ganze Zahl sein.

Wenn eine ganze Zahl zu einem Zeiger addiert wird, wird der Ganzzahlwert (*i*) konvertiert, indem er mit der Größe des Werts multipliziert wird, auf den der Zeiger zeigt. Nach der Konvertierung stellt der ganzzahlige Wert *i* Arbeitsspeicherpositionen dar, wobei jede Position über die Länge verfügt, die vom Zeigertyp angegeben wird. Wenn der konvertierte Ganzzahlwert zum Zeigerwert addiert wird, ist das Ergebnis ein neuer Zeigerwert, der die Adresse in der Entfernung von *i* Positionen von der ursprünglichen Adresse darstellt. Der neue Zeigerwert gibt den Wert desselben Typs an, der vom ursprüngliche Zeigerwert adressiert wurde. Dieser Wert gleicht der Arrayindizierung (siehe [Eindimensionale Arrays](../c-language/one-dimensional-arrays.md) und [Mehrdimensionale Arrays](../c-language/multidimensional-arrays-c.md)). Wenn der Summenzeiger über das Array hinaus zeigt (außer auf die erste Position oberhalb des oberen Grenzwerts), ist das Ergebnis nicht definiert. Weitere Informationen finden Sie unter [Zeigerarithmetik](../c-language/pointer-arithmetic.md).

## <a name="see-also"></a>Siehe auch

[C-Operatoren (additiv)](../c-language/c-additive-operators.md)
