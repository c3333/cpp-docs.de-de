---
title: Ausdrücke in Klammern
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: d0105556530161991b46c5ee25cd73f2f995063f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233740"
---
# <a name="expressions-in-parentheses"></a>Ausdrücke in Klammern

Sie können jeden Operanden in Klammern einschließen, ohne den Typ oder den Wert des eingeschlossenen Ausdrucks zu ändern. Als Beispiel dient der folgende Ausdruck:

```
( 10 + 5 ) / 5
```

Die Klammern um `10 + 5` bedeuten, dass der Wert von `10 + 5` zuerst ausgewertet und dann zum linken Operanden des Divisionsoperators ( **/** ) wird. Das Ergebnis von `( 10 + 5 ) / 5` lautet 3. Ohne die Klammern würde `10 + 5 / 5` als 11 ausgewertet werden.

Obwohl Klammern die Methode beeinflussen, wie die Operanden in einem Ausdruck gruppiert werden, können sie keine bestimmte Auswertungsreihenfolge in allen Fällen garantieren. Zum Beispiel stellen weder die Klammern noch die Gruppierung des folgenden Ausdrucks von links nach rechts den Wert von `i` in einem der Unterausdrücke sicher:

```
( i++ +1 ) * ( 2 + i )
```

Der Compiler kann die beiden Seiten der Multiplikation in beliebiger Reihenfolge auswerten. Wenn der Anfangswert von `i` 0 (null) ist, kann der gesamte Ausdruck als eine dieser beiden Anweisungen ausgewertet werden:

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Die Ausnahmen, die durch Nebeneffekte auftreten, werden in [Nebeneffekte](../c-language/side-effects.md) erläutert.

## <a name="see-also"></a>Siehe auch

[C-Ausdrücke (primär)](../c-language/c-primary-expressions.md)
