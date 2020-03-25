---
title: 'Gleichheitsoperatoren: == und !='
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 8a0c08f438528caeaac6d5e52e806a36fe56dd25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189246"
---
# <a name="equality-operators--and-"></a>Gleichheitsoperatoren: == und !=

## <a name="syntax"></a>Syntax

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Bemerkungen

Die binären Gleichheitsoperatoren vergleichen die Operanden hinsichtlich strikter Gleichheit oder Ungleichheit.

Die Gleichheitsoperatoren "gleich" (`==`) und "ungleich" (`!=`) haben weniger Vorrang als die relationalen Operatoren, aber sie verhalten sich ähnlich. Der Ergebnistyp für diese Operatoren ist " **bool**".

Der Gleichheits Operator (`==`) gibt **true** (1) zurück, wenn beide Operanden denselben Wert aufweisen. Andernfalls wird **false** (0) zurückgegeben. Der ungleich Operator (`!=`) gibt **true** zurück, wenn die Operanden nicht denselben Wert aufweisen. Andernfalls wird **false**zurückgegeben.

## <a name="operator-keyword-for-"></a>Operator-Schlüsselwort für !=

Der `not_eq`-Operator ist die Textentsprechung von `!=`. Es gibt zwei Möglichkeiten, auf den `not_eq`-Operator in ihren Programmen zuzugreifen: Fügen Sie die Header Datei `iso646.h`ein, oder kompilieren Sie mit der Compileroption [/Za](../build/reference/za-ze-disable-language-extensions.md) (Spracherweiterungen deaktivieren).

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

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren (relational) und C-Gleichheitsoperatoren](../c-language/c-relational-and-equality-operators.md)
