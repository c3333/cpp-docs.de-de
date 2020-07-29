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
ms.openlocfilehash: a21c62549f02dddda951c79a06617671ccfe2526
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227217"
---
# <a name="overloading-unary-operators"></a>Überladen von unären Operatoren

Die unären Operatoren, die überladen werden können, sind Folgende:

1. `!`([Logisches Not](../cpp/logical-negation-operator-exclpt.md))

1. `&`([Adresse von](../cpp/address-of-operator-amp.md))

1. `~`([Einerkomplement](../cpp/one-s-complement-operator-tilde.md))

1. `*`([Zeigerdereferenzierung](../cpp/indirection-operator-star.md))

1. `+`([unäres Plus](../cpp/additive-operators-plus-and.md))

1. `-`([unäre Negation](../cpp/additive-operators-plus-and.md))

1. `++`([Inkrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([Dekrement](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. Konvertierungsoperatoren

Die Postfix-Inkrement-und Dekrementoperatoren ( `++` und `--` ) werden separat in [Inkrement-und Dekrementoperatoren](../cpp/increment-and-decrement-operator-overloading-cpp.md)behandelt.

Konvertierungs Operatoren werden auch in einem separaten Thema behandelt. siehe [benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md).

Die folgenden Regeln sind für alle anderen unären Operatoren erfüllt. Um eine Funktion für einen unären Operator als nicht statischen Member zu deklarieren, müssen Sie sie im folgenden Format deklarieren:

> *ret-Typ* **`operator`** *op* **()**

wobei " *ret-Type* " der Rückgabetyp und " *op* " einer der in der obigen Tabelle aufgeführten Operatoren ist.

Um eine Funktion für einen unären Operator als globale Funktion zu deklarieren, müssen Sie sie im folgenden Format deklarieren:

> *ret-Typ* **`operator`** *op* **(** *arg* **)**

Dabei sind " *ret-Type* " und " *op* " wie für Member-Operator Funktionen beschrieben und " *arg* " ein Argument des Klassen Typs, in dem der Vorgang ausgeführt werden soll.

> [!NOTE]
> Es gibt keine Einschränkung für die Rückgabetypen der unären Operatoren. Beispielsweise macht es Sinn für ein logisches NOT (`!`), einen Ganzzahlwert zurückzugeben. Das wird aber nicht erzwungen.

## <a name="see-also"></a>Siehe auch

[Operator Überladung](../cpp/operator-overloading.md)
