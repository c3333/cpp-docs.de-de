---
title: 'Logischer Negationsoperator: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446542"
---
# <a name="logical-negation-operator-"></a>Logischer Negationsoperator: !

## <a name="syntax"></a>Syntax

```
! cast-expression
```

## <a name="remarks"></a>Bemerkungen

Der logische Negations Operator ( **!** ) kehrt die Bedeutung seines Operanden um. Der Operand muss ein arithmetischer Typ oder Zeigertyp sein (oder ein Ausdruck, der dem arithmetischen Typ oder dem Zeigertyp gleicht). Der Operand wird implizit in den Typ **bool**konvertiert. Das Ergebnis ist true, wenn der konvertierte Operand false ist. Das Ergebnis ist false, wenn der konvertierte Operand true ist. Das Ergebnis ist vom Typ " **bool**".

Bei einem Ausdruck *e*entspricht der `!e` des unären Ausdrucks dem Ausdruck `(e == 0)`, mit dem Unterschied, dass überladene Operatoren beteiligt sind.

## <a name="operator-keyword-for-"></a>Operator-Schlüsselwort für "!"

Der **Not** -Operator ist eine alternative Schreibweise von **!** . Es gibt zwei Möglichkeiten, auf den **Not** -Operator in ihren Programmen zuzugreifen: Fügen Sie die Header Datei \<iso646. h > ein, oder kompilieren Sie mit der [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption (Spracherweiterungen deaktivieren).

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

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md)<br/>
