---
title: 'Bitweiser Operator für inklusives ODER: |'
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 0df3493930206d655c0d9bca8a2468151aa3c2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445509"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitweiser Operator für inklusives ODER: |

## <a name="syntax"></a>Syntax

> *expression1* **|** *expression2*

## <a name="remarks"></a>Bemerkungen

Der bitweise inklusive OR-Operator ( **&#124;** ) vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn eines der Bits 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 festgelegt.

Beide Operanden im bitweisen inklusiven OR-Operator müssen vom Ganzzahltyp sein. Die üblichen arithmetischen Konvertierungen, die in [Standard Konvertierungen](standard-conversions.md) abgedeckt werden, werden auf die Operanden angewendet.

## <a name="operator-keyword-for-124"></a>Operator Schlüsselwort für&#124;

Der **bitor** -Operator ist die Text Entsprechung von **&#124;** . Es gibt zwei Möglichkeiten, auf den **bitor** -Operator in ihren Programmen zuzugreifen: Schließen Sie die Header Datei \<iso646. h > ein, oder kompilieren Sie mit der [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption (Spracherweiterungen deaktivieren).

## <a name="example"></a>Beispiel

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren zur Bitmanipulation](../c-language/c-bitwise-operators.md)