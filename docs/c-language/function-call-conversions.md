---
title: Funktionsaufrufkonvertierungen
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233218"
---
# <a name="function-call-conversions"></a>Funktionsaufrufkonvertierungen

Der Konvertierungstyp, der an Argumenten in einem Funktionsaufruf ausgeführt wird, hängt von der Anwesenheit eines Funktionsprototyps (Vorwärtsdeklaration) mit deklarierten Argumenttypen für die aufgerufene Funktion ab.

Wenn ein Funktionsprototyp vorhanden ist und deklarierte Argumenttypen enthält, führt der Compiler die Typüberprüfung aus (siehe [Funktionen](../c-language/functions-c.md)).

Wenn kein Funktionsprototyp vorhanden ist, werden nur die üblichen arithmetischen Konvertierungen mit den Argumenten im Funktionsaufruf ausgeführt. Diese Konvertierungen werden für jedes Argument im Aufruf unabhängig ausgeführt. Dies bedeutet, dass ein **float**-Wert in einen **double**-Wert, ein `char`- oder **short**-Wert in einen `int`-Wert und ein `unsigned char`- oder **unsigned short**-Wert in einen `unsigned int`-Wert konvertiert wird.

## <a name="see-also"></a>Siehe auch

[Typkonvertierungen](../c-language/type-conversions-c.md)
