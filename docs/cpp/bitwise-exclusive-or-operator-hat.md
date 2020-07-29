---
title: 'Bitweiser Operator für exklusives ODER: ^'
description: Die exklusive Syntax der C++-Standardsprache oder-Operator Syntax und die Verwendung.
ms.date: 07/23/2020
f1_keywords:
- xor_cpp
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 0f64b9f90b70756d29fcabb361cc07abe58e0a54
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229102"
---
# <a name="bitwise-exclusive-or-operator-"></a>Bitweiser Operator für exklusives ODER: ^

## <a name="syntax"></a>Syntax

> *Ausdruck* **`^`** *Ausdruck*

## <a name="remarks"></a>Bemerkungen

Der bitweise exklusive OR-Operator ( **`^`** ) vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn das Bit im ersten Operanden 0 und das andere Bit 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.

Beide Operanden für den Operator müssen ganzzahlige Typen aufweisen. Die üblichen arithmetischen Konvertierungen, die in [Standard Konvertierungen](standard-conversions.md) abgedeckt werden, werden auf die Operanden angewendet.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für ^

C++ gibt **`xor`** als Alternative Schreibweise für an **`^`** . In C wird die alternative Schreibweise als Makro in der \<iso646.h> Kopfzeile bereitgestellt. In C++ ist die alternative Schreibweise ein Schlüsselwort. die Verwendung von \<iso646.h> oder der C++-Entsprechung \<ciso646> ist als veraltet markiert. In Microsoft C++ ist die- [`/permissive-`](../build/reference/permissive-standards-conformance.md) oder- [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Compileroption erforderlich, um die alternative Schreibweise zu aktivieren.


## <a name="example"></a>Beispiel

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>Siehe auch

[C++ integrierte Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
