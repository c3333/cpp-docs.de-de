---
title: Überladen von unären Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372034"
---
# <a name="overloading-unary-operators"></a>Überladen von unären Operatoren

Die unären Operatoren, die überladen werden können, sind Folgende:

1. `!`([logisch NICHT](../cpp/logical-negation-operator-exclpt.md))

1. `&`([Adresse)](../cpp/address-of-operator-amp.md)

1. `~`([die Komplement )](../cpp/one-s-complement-operator-tilde.md)

1. `*`([Zeigerdereferenzierung](../cpp/indirection-operator-star.md))

1. `+`([unary plus](../cpp/additive-operators-plus-and.md))

1. `-`([unäre Negation](../cpp/additive-operators-plus-and.md))

1. `++`([Inkrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([dekrementierung](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. Konvertierungsoperatoren

Die Postfix-Inkrement-`++` und `--`Dekrementoperatoren ( und ) werden in [Increment und Dekrement](../cpp/increment-and-decrement-operator-overloading-cpp.md)separat behandelt.

Konvertierungsoperatoren werden auch in einem separaten Thema behandelt. siehe [Benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md).

Die folgenden Regeln sind für alle anderen unären Operatoren erfüllt. Um eine Funktion für einen unären Operator als nicht statischen Member zu deklarieren, müssen Sie sie im folgenden Format deklarieren:

> *ret-Typ* **Operator** *op* **()**

wobei *ret-type* der Rückgabetyp ist und *op* einer der in der obigen Tabelle aufgeführten Operatoren ist.

Um eine Funktion für einen unären Operator als globale Funktion zu deklarieren, müssen Sie sie im folgenden Format deklarieren:

> *ret-typ* **operator** *op* **(** *arg* **)**

wobei *ret-type* und *op* wie für Memberoperatorfunktionen beschrieben sind und der *arg* ein Argument des Klassentyps ist, auf dem ausgeführt werden soll.

> [!NOTE]
> Es gibt keine Einschränkung für die Rückgabetypen der unären Operatoren. Beispielsweise macht es Sinn für ein logisches NOT (`!`), einen Ganzzahlwert zurückzugeben. Das wird aber nicht erzwungen.

## <a name="see-also"></a>Siehe auch

[Operatorüberladung](../cpp/operator-overloading.md)
