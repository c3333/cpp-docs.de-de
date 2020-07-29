---
title: 'Einerkomplementoperator: ~'
description: Die Syntax und Verwendung der C++-Standardsprache eines-Komplement Operators.
ms.date: 07/23/2020
f1_keywords:
- "~"
- compl_cpp
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 89c67855cd67df2af315cea941b487e7462889b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227243"
---
# <a name="ones-complement-operator-"></a>Einerkomplementoperator: ~

## <a name="syntax"></a>Syntax

```cpp
~ cast-expression
```

## <a name="remarks"></a>Bemerkungen

Der Einerkomplementoperator ( **`~`** ), der manchmal als *bitweiser Komplement* Operator bezeichnet wird, ergibt eine bitweise Einerkomplement seines Operanden. Das bedeutet, dass jedes Bit, das 1 im Operanden ist, 0 im Ergebnis ist. Umgekehrt ist jedes Bit, das 0 im Operanden ist, im Ergebnis 1. Der Operand für den Einerkomplementoperator muss ein ganzzahliger Typ sein.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für ~

C++ gibt **`compl`** als Alternative Schreibweise für an **`~`** . In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

In diesem Beispiel ist der neue Wert, der `y` zugewiesen ist, das Einerkomplement des Werts ohne Vorzeichen 0xFFFF oder 0x0000.

Ganzzahlige Erweiterung wird für ganzzahlige Operanden ausgeführt. Der Typ, zu dem der Operand herauf gestuft wird, ist der resultierende Typ. Weitere Informationen zur ganzzahligen herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md).

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](expressions-with-unary-operators.md)<br/>
[C++ integrierte Operatoren, Rangfolge und Assoziativität](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md)
