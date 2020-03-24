---
title: 'Dereferenzierungsoperator: *'
ms.date: 11/04/2016
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
ms.openlocfilehash: 8f27cfd943455d52b04c41ef2d2d83e6e03a84c0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178276"
---
# <a name="indirection-operator-"></a>Dereferenzierungsoperator: *

## <a name="syntax"></a>Syntax

```
* cast-expression
```

## <a name="remarks"></a>Bemerkungen

Der unäre Dereferenzierungsoperator (<strong>\*</strong>) dereferenziert einen Zeiger. Das heißt, dass ein Zeiger Wert in einen l-Wert konvertiert wird. Der Operand des Dereferenzierungsoperators muss ein Zeiger auf einen Typ sein. Das Ergebnis des Dereferenzierungsausdrucks ist der Typ, aus dem der Zeigertyp abgeleitet wird. Die Verwendung des <strong>\*</strong> Operators in diesem Kontext unterscheidet sich von der Bedeutung als binärer Operator, der Multiplikation ist.

Wenn der Operand auf eine Funktion verweist, ist das Ergebnis ein Funktionsbezeichner. Wenn an einen Speicherort verwiesen wird, ist das Ergebnis ein l-Wert, der den Speicherort festlegt.

Der Dereferenzierungsoperator kann kumulativ verwendet werden, um Zeiger zu Zeigern zu dereferenzieren. Beispiel:

```cpp
// expre_Indirection_Operator.cpp
// compile with: /EHsc
// Demonstrate indirection operator
#include <iostream>
using namespace std;
int main() {
   int n = 5;
   int *pn = &n;
   int **ppn = &pn;

   cout  << "Value of n:\n"
         << "direct value: " << n << endl
         << "indirect value: " << *pn << endl
         << "doubly indirect value: " << **ppn << endl
         << "address of n: " << pn << endl
         << "address of n via indirection: " << *ppn << endl;
}
```

Wenn der Zeigerwert ungültig ist, ist das Ergebnis nicht definiert. Die folgende Liste umfasst einige der häufigsten Bedingungen, die einen Zeigerwert ungültig machen.

- Der Zeiger ist ein NULL-Zeiger.

- Der Zeiger gibt die Adresse eines lokalen Elements an, das zum Zeitpunkt des Verweises nicht sichtbar ist.

- Der Zeiger gibt eine Adresse an, die nicht ordnungsgemäß auf den Objekttyp, auf den gezeigt wird, ausgerichtet ist.

- Der Zeiger gibt eine Adresse an, die nicht vom ausgeführten Programm verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[address-of-Operator](../cpp/address-of-operator-amp.md)<br/>
[Dereferenzierungs- und Address-of-Operatoren](../c-language/indirection-and-address-of-operators.md)
