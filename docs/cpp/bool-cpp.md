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
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190494"
---
# <a name="bool-c"></a>bool (C++)

Dieses Schlüsselwort ist ein integrierter Typ. Eine Variable dieses Typs kann die Werte [true](../cpp/true-cpp.md) und [false](../cpp/false-cpp.md)aufweisen. Bedingte Ausdrücke weisen den Typ **bool** auf und verfügen daher über Werte vom Typ **bool**. Beispielsweise ist `i!=0` jetzt "true" oder "false", abhängig vom Wert `i`.

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): der Operand eines Postfix-oder Präfix Inkrement-oder Dekrementoperators ist möglicherweise nicht vom Typ **bool**. Anders ausgedrückt: Wenn eine Variable `b` vom Typ " **bool**" ist, sind diese Ausdrücke nicht mehr zulässig:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Die Werte "true" und "false" haben die folgende Beziehung:

```cpp
!false == true
!true == false
```

Betrachten Sie folgende Anweisung:

```cpp
if (condexpr1) statement1;
```

Wenn `condexpr1` true ist, wird `statement1` immer ausgeführt. Wenn `condexpr1` false ist, wird `statement1` nie ausgeführt.

Wenn ein postfix-oder Präfix **++** -Operator auf eine Variable des Typs **bool**angewendet wird, wird die Variable auf true festgelegt.
**Visual Studio 2017 Version 15,3 und**höher: Operator + + für **bool** wurde aus der Sprache entfernt und wird nicht mehr unterstützt.

Der Postfix-oder Präfix **--** -Operator kann nicht auf eine Variable dieses Typs angewendet werden.

Der **bool** -Typ nimmt an ganzzahligen Erweiterungen Teil. Ein r-Wert des Typs " **bool** " kann in einen r-Wert vom Typ " **int**" konvertiert werden, wobei "false" 0 (null) und "true" ist. Als eindeutiger Typ nimmt **bool** an der Überladungs Auflösung Teil.

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Integrierte Typen](../cpp/fundamental-types-cpp.md)
