---
title: 'Bitweiser Operator für exklusives ODER: ^'
description: Die exklusive Syntax der C++-Standardsprache oder-Operator Syntax und die Verwendung.
ms.date: 09/21/2020
f1_keywords:
- xor_cpp
- ^
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 4823c245ffca7032347e37c0c25c2963407733a7
ms.sourcegitcommit: f656092eebbcb148ca4d3b7a6a8508eff8f7e85f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2020
ms.locfileid: "90836627"
---
# <a name="bitwise-exclusive-or-operator-"></a>Bitweiser Operator für exklusives ODER: ^

## <a name="syntax"></a>Syntax

> *Ausdruck* **`^`** *Ausdruck*

## <a name="remarks"></a>Bemerkungen

Der bitweise exklusive OR-Operator ( **`^`** ) vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn das Bit in einem der Operanden 0 und das Bit im anderen Operanden 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.

Beide Operanden für den Operator müssen ganzzahlige Typen aufweisen. Die üblichen arithmetischen Konvertierungen, die in [Standard Konvertierungen](standard-conversions.md) abgedeckt werden, werden auf die Operanden angewendet.

Weitere Informationen zur alternativen Verwendung des **`^`** Zeichens in C++/CLI und C++/CX finden [Sie unter handle to Object Operator (^) (C++/CLI und C++/CX)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

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
