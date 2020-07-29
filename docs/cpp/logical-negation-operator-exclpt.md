---
title: 'Logischer Negationsoperator: !'
description: Die Syntax und Verwendung des logischen Negations Operators der C++-Standardsprache.
ms.date: 07/23/2020
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: fdd2e7a71b791375f898372d058a5eeb2afc59f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223680"
---
# <a name="logical-negation-operator-"></a>Logischer Negationsoperator: !

## <a name="syntax"></a>Syntax

> **`!`***Cast-Ausdruck*

## <a name="remarks"></a>Bemerkungen

Der logische Negations Operator ( **`!`** ) kehrt die Bedeutung seines Operanden um. Der Operand muss ein arithmetischer Typ oder Zeigertyp sein (oder ein Ausdruck, der dem arithmetischen Typ oder dem Zeigertyp gleicht). Der Operand wird implizit in den Typ konvertiert **`bool`** . Das Ergebnis ist **`true`** , wenn der konvertierte Operand ist **`false`** . das Ergebnis ist, **`false`** Wenn der konvertierte Operand ist **`true`** . Das Ergebnis ist vom Typ **`bool`** .

Bei einem Ausdruck `e` entspricht der unäre Ausdruck `!e` dem Ausdruck, mit dem Unterschied `(e == 0)` , dass überladene Operatoren beteiligt sind.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für!

C++ gibt **`not`** als Alternative Schreibweise für an **`!`** . In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++ integrierte Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md)<br/>
