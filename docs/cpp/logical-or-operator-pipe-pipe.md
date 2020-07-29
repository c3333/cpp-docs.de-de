---
title: 'Logischer or-Operator:  &#124;&#124;'
description: Die C++-Standardsprache der logischen OR-Operator Syntax und verwenden.
ms.date: 07/23/2020
f1_keywords:
- '||'
- or_cpp
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 1845aef59f88d5dd044cefedd21cb618e1102e13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225994"
---
# <a name="logical-or-operator-124124"></a>Logischer or-Operator:  &#124;&#124;

## <a name="syntax"></a>Syntax

> *logischer or-Ausdruck* **`||`** *logischer and-Ausdruck*

## <a name="remarks"></a>Bemerkungen

Der logische OR-Operator ( **`||`** ) gibt den booleschen Wert zurück, wenn einer der **`true`** Operanden oder beide Operanden ist, **`true`** und gibt **`false`** andernfalls zurück. Die Operanden werden vor der Auswertung implizit in den Typ konvertiert **`bool`** , und das Ergebnis ist vom Typ **`bool`** . Das logische OR weist eine Assoziativität von links nach rechts auf.

Die Operanden für den logischen OR-Operator müssen nicht denselben Typ aufweisen, aber Sie müssen einen booleschen, ganzzahligen oder Zeigertyp aufweisen. Die Operanden sind im Allgemeinen relationale oder Gleichheitsausdrücke.

Der erste Operand wird vollständig ausgewertet und alle Nebeneffekte werden abgeschlossen, bevor die Auswertung des logischen OR-Ausdrucks fortgesetzt wird.

Der zweite Operand wird nur ausgewertet, wenn der erste Operand als ausgewertet wird **`false`** , da die Auswertung nicht erforderlich ist, wenn der logische OR-Ausdruck ist **`true`** . Dies wird als *Kurzschluss* Auswertung bezeichnet.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Im obigen Beispiel, wenn `x` gleich `w` , oder ist, wird `y` `z` das zweite Argument für die- `printf` Funktion als ausgewertet **`true`** , das dann zu einer Ganzzahl herauf gestuft wird, und der Wert 1 wird gedruckt. Andernfalls wird zu ausgewertet, **`false`** und der Wert 0 wird gedruckt. Sobald eine der Bedingungen ergibt **`true`** , wird die Auswertung beendet.

## <a name="operator-keyword-for-124124"></a>Operator Schlüsselwort für &#124;&#124;

C++ gibt **`or`** als Alternative Schreibweise für an **`||`** . In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Siehe auch

[C++ integrierte Operatoren, Rangfolge und Assoziativität](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Logische C-Operatoren](../c-language/c-logical-operators.md)
