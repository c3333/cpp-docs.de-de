---
title: 'Gleichheitsoperatoren: == und !='
description: Die C++-Standardsprache der Operator Syntax und die nicht-gleich-Operator Syntax und verwenden.
ms.date: 07/23/2020
f1_keywords:
- '!='
- ==
- not_eq_cpp
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 567b83e99dce0354626f08a4788f1343314493b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227542"
---
# <a name="equality-operators--and-"></a>Gleichheitsoperatoren: == und !=

## <a name="syntax"></a>Syntax

> *Ausdruck* **`==`** *Ausdruck*\
> *Ausdruck* **`!=`** *Ausdruck*

## <a name="remarks"></a>Bemerkungen

Die binären Gleichheitsoperatoren vergleichen die Operanden hinsichtlich strikter Gleichheit oder Ungleichheit.

Die Gleichheits Operatoren gleich ( **`==`** ) und ungleich ( **`!=`** ) haben Vorrang vor den relationalen Operatoren, aber Sie Verhalten sich ähnlich. Der Ergebnistyp für diese Operatoren ist **`bool`** .

Der Gleichheits Operator ( **`==`** ) gibt zurück **`true`** , wenn beide Operanden denselben Wert aufweisen; andernfalls wird zurückgegeben **`false`** . Der ungleich Operator ( **`!=`** ) gibt zurück **`true`** , wenn die Operanden nicht denselben Wert aufweisen; andernfalls wird zurückgegeben **`false`** .

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für! =

C++ gibt **`not_eq`** als Alternative Schreibweise für an **`!=`** . (Es gibt keine Alternative Schreibweise für **`==`** .) In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.

## <a name="example"></a>Beispiel

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

Gleichheitsoperatoren können Zeiger auf Member des gleichen Typs vergleichen. In einem solchen Vergleich werden Pointer-to-Member-Konvertierungen ausgeführt. Pointer-to-member können auch mit einem konstanten Ausdruck verglichen werden, der mit 0 ausgewertet wird.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge; und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Relationale C-Operatoren und C-Gleichheitsoperatoren](../c-language/c-relational-and-equality-operators.md)
