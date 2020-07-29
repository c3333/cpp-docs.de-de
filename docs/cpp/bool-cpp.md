---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: 8cd035686a07285f52fe24aa7ab4f360619d5e1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229076"
---
# <a name="bool-c"></a>bool (C++)

Dieses Schlüsselwort ist ein integrierter Typ. Eine Variable dieses Typs kann über Werte [`true`](../cpp/true-cpp.md) und verfügen [`false`](../cpp/false-cpp.md) . Bedingte Ausdrücke weisen den **`bool`** -Typ auf und verfügen daher über Werte vom Typ **`bool`** . Beispielsweise `i != 0` ist nun **`true`** oder **`false`** abhängig vom Wert von `i` .

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): der Operand eines Postfix-oder Präfix Inkrement-oder Dekrementoperators ist möglicherweise nicht vom Typ **`bool`** . Anders ausgedrückt: Wenn eine Variable `b` vom Typ **`bool`** ist, sind diese Ausdrücke nicht mehr zulässig:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Die Werte **`true`** und **`false`** haben die folgende Beziehung:

```cpp
!false == true
!true == false
```

Betrachten Sie folgende Anweisung:

```cpp
if (condexpr1) statement1;
```

Wenn `condexpr1` ist **`true`** , `statement1` wird immer ausgeführt; wenn `condexpr1` ist **`false`** , `statement1` wird nie ausgeführt.

Wenn ein postfix-oder Präfix- **`++`** Operator auf eine Variable vom Typ angewendet wird **`bool`** , wird die Variable auf festgelegt **`true`** .

**Visual Studio 2017 Version 15,3 und**höher: `operator++` für **`bool`** wurde aus der Sprache entfernt und wird nicht mehr unterstützt.

Der Postfix-oder Präfix **`--`** Operator kann nicht auf eine Variable dieses Typs angewendet werden.

Der **`bool`** Typ nimmt an standardmäßigen ganzzahligen Erweiterungen Teil. Ein r-Wert des Typs **`bool`** kann in einen r-Wert des Typs konvertiert werden **`int`** , wobei **`false`** 0 (null) und **`true`** 1 wird. Als eindeutiger Typ ist **`bool`** an der Überladungs Auflösung beteiligt.

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Integrierte Typen](../cpp/fundamental-types-cpp.md)
