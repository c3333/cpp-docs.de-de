---
title: Bezeichner in primären Ausdrücken
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 053720bcdf635a7e09363712259b558d93a2972c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233085"
---
# <a name="identifiers-in-primary-expressions"></a>Bezeichner in primären Ausdrücken

Bezeichner können folgende Typen haben: ganzzahlig, **Float**, `enum`, `struct`, **Union**, Array, Zeiger oder Funktionstyp. Ein Bezeichner ist ein primärer Ausdruck, vorausgesetzt, er wurde als Festlegen eines Objekts deklariert (in diesem Fall ein l-Wert) oder als Funktion (in diesem Fall ist es ein Funktionsbezeichner). Eine Definition des l-Werts finden Sie unter [L-Wert- und R-Wert-Ausdrücke](../c-language/l-value-and-r-value-expressions.md).

Der Zeigerwert, der durch einen Arraybezeichner dargestellt wird, ist keine Variable. Daher kann der Arraybezeichner nicht den linken Operanden eines Zuweisungsvorgangs bilden und ist kein änderbarer L-Wert.

Ein Bezeichner, der als Funktion deklariert wurde, stellt einen Zeiger dar, dessen Wert die Adresse der Funktion darstellt. Der Zeiger adressiert eine Funktion, die einen Wert eines bestimmten Typs zurückgibt. Daher dürfen Funktionsbezeichner auch keine L-Werte in Zuweisungsvorgängen sein. Weitere Informationen finden Sie unter [Identifiers](../c-language/c-identifiers.md).

## <a name="see-also"></a>Siehe auch

[C-Ausdrücke (primär)](../c-language/c-primary-expressions.md)
