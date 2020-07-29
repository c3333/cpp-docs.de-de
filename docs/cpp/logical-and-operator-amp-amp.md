---
title: Logischer and-Operator:&amp;&amp;
description: Die logische And-Operator Syntax der C++-Standardsprache und die Verwendung von.
ms.date: 07/23/2020
f1_keywords:
- '&&'
- and_cpp
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 431e76a2943c2373d6191f1fbe9f14c54cfaa6c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223693"
---
# <a name="logical-and-operator-ampamp"></a>Logischer and-Operator:&amp;&amp;

## <a name="syntax"></a>Syntax

> *Ausdruck* **`&&`** *Ausdruck*

## <a name="remarks"></a>Bemerkungen

Der logische And-Operator ( **&&** ) gibt zurück, **`true`** Wenn beide Operanden sind, **`true`** und gibt **`false`** andernfalls zurück. Die Operanden werden vor der Auswertung implizit in den Typ konvertiert **`bool`** , und das Ergebnis ist vom Typ **`bool`** . Das logische AND weist eine Assoziativität von links nach rechts auf.

Die Operanden für den logischen AND-Operator müssen nicht denselben Typ aufweisen, aber Sie müssen einen booleschen, ganzzahligen oder Zeigertyp aufweisen. Die Operanden sind im Allgemeinen relationale oder Gleichheitsausdrücke.

Der erste Operand wird vollständig ausgewertet, und alle Nebeneffekte werden abgeschlossen, bevor die Auswertung des logischen and-Ausdrucks fortgesetzt wird.

Der zweite Operand wird nur ausgewertet, wenn der erste Operand als **`true`** (ungleich null) ausgewertet wird. Diese Auswertung eliminiert die unnötige Auswertung des zweiten Operanden, wenn der logische and-Ausdruck ist **`false`** . Mithilfe dieser Kurzschlussauswertung können Sie Dereferenzierungen durch NULL-Zeiger verhindern, wie im folgenden Beispiel gezeigt:

```cpp
char *pch = 0;
// ...
(pch) && (*pch = 'a');
```

Wenn `pch` null (0) ist, wird die rechte Seite des Ausdrucks niemals ausgewertet. Diese Kurzschluss Auswertung macht die Zuweisung durch einen NULL-Zeiger unmöglich.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für &&

C++ gibt **`and`** als Alternative Schreibweise für an **`&&`** . In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Siehe auch

[C++ integrierte Operatoren, Rangfolge und Assoziativität](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logische C-Operatoren](../c-language/c-logical-operators.md)
