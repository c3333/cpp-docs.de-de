---
title: Ausdrucksanweisung
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2f12bbbafd9be50f851e36f472098431f9ac0d5d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188999"
---
# <a name="expression-statement"></a>Ausdrucksanweisung

Ausdrucksanweisungen bewirken die Auswertung von Ausdrücken. Keine Übertragung der Steuerung oder Iteration tritt infolge einer Ausdrucksanweisung auf.

Die Syntax für die Ausdrucksanweisung ist einfach

## <a name="syntax"></a>Syntax

```
[expression ] ;
```

## <a name="remarks"></a>Bemerkungen

Alle Ausdrücke in einer Ausdrucksanweisung werden ausgewertet und alle Nebeneffekte werden abgeschlossen, bevor die nächste Anweisung ausgeführt wird. Die häufigsten Ausdrucksanweisungen sind Zuweisungen und Funktionsaufrufe.  Da der Ausdruck optional ist, wird ein Semikolon allein als leere Ausdrucks Anweisung betrachtet, die als [null](../cpp/null-statement.md) -Anweisung bezeichnet wird.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über C++-Anweisungen](../cpp/overview-of-cpp-statements.md)
