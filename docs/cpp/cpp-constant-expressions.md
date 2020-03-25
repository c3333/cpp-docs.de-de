---
title: C++-Ausdrücke (konstant)
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: d4d9803c7f80caba3c33d011e4df433491b9b591
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170578"
---
# <a name="c-constant-expressions"></a>C++-Ausdrücke (konstant)

Ein *konstanter* Wert ist ein Wert, der nicht geändert wird. C++ bietet zwei Schlüsselwörter, mit denen Sie den Zweck eines Objekts angeben können, der nicht dazu gedacht ist, geändert zu werden, und diese Absicht erzwingen soll.

C++ erfordert konstante Ausdrücke – Ausdrücke, die als Konstante ausgewertet werden – für Deklarationen von:

- Arraygrenzen

- Selektoren in case-Anweisungen

- Bitfeldlängenangabe

- Enumerationsinitialisierer

Die einzigen Operanden, die in konstanten Ausdrücken zulässig sind, lauten:

- Literale

- Enumerationskonstanten

- Werte, die als Konstanten deklariert sind und mit konstanten Ausdrücken initialisiert werden.

- **sizeof** -Ausdrücke

Konstanten, die keine Ganzzahlen sind, müssen (entweder explizit oder implizit) in ganzzahlige Typen konvertiert werden, um in einem konstanten Ausdruck zulässig zu sein. Daher ist der folgende Code gültig:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Explizite Konvertierungen in ganzzahlige Typen sind in konstanten Ausdrücken zulässig. alle anderen Typen und abgeleiteten Typen sind unzulässig, außer wenn Sie als Operanden für den **sizeof** -Operator verwendet werden.

Der Kommaoperator sowie Zuweisungsoperatoren können nicht in konstanten Ausdrücken verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[Ausdruckstypen](../cpp/types-of-expressions.md)
