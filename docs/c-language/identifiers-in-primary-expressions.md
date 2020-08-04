---
title: Bezeichner in primären Ausdrücken
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: a6ad5a47230c6ba4bb2c0d636e50779b65483875
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229661"
---
# <a name="identifiers-in-primary-expressions"></a>Bezeichner in primären Ausdrücken

Bezeichner können folgende Typen haben: ganzzahlig, **`float`** , **`enum`** , **`struct`** , **`union`** , Array, Zeiger oder Funktion. Ein Bezeichner ist ein primärer Ausdruck, vorausgesetzt, er wurde als Festlegen eines Objekts deklariert (in diesem Fall ein l-Wert) oder als Funktion (in diesem Fall ist es ein Funktionsbezeichner). Eine Definition des l-Werts finden Sie unter [L-Wert- und R-Wert-Ausdrücke](../c-language/l-value-and-r-value-expressions.md).

Der Zeigerwert, der durch einen Arraybezeichner dargestellt wird, ist keine Variable. Daher kann der Arraybezeichner nicht den linken Operanden eines Zuweisungsvorgangs bilden und ist kein änderbarer L-Wert.

Ein Bezeichner, der als Funktion deklariert wurde, stellt einen Zeiger dar, dessen Wert die Adresse der Funktion darstellt. Der Zeiger adressiert eine Funktion, die einen Wert eines bestimmten Typs zurückgibt. Daher dürfen Funktionsbezeichner auch keine L-Werte in Zuweisungsvorgängen sein. Weitere Informationen finden Sie unter [Identifiers](../c-language/c-identifiers.md).

## <a name="see-also"></a>Siehe auch

[C-Ausdrücke (primär)](../c-language/c-primary-expressions.md)
