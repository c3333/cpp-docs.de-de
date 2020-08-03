---
title: Unsachgemäßer Zugriff auf eine Union
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 5a804ed80c8f1ac2f5dd9a24f12c67e96e199b6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227828"
---
# <a name="improper-access-to-a-union"></a>Unsachgemäßer Zugriff auf eine Union

**ANSI 3.3.2.3** Auf ein Member eines union-Objekts wird mithilfe eines Members eines anderen Typs zugegriffen

Wenn eine Union von zwei Typen deklariert wird und ein Wert gespeichert ist, aber mit dem anderen Typ auf die Union zugegriffen wird, sind die Ergebnisse unzuverlässig.

Beispielsweise wird eine Union von **`float`** und **`int`** deklariert. Ein **`float`** -Wert wird gespeichert, aber später greift das Programm auf den Wert als **`int`** zu. In einer solchen Situation ist der Wert von der internen Speicherung von **`float`** -Werten abhängig. Der Ganzzahlwert wäre nicht zuverlässig.

## <a name="see-also"></a>Siehe auch

[Strukturen, Unions, Enumerationen und Bitfelder](../c-language/structures-unions-enumerations-and-bit-fields.md)
