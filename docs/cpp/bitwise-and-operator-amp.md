---
title: 'Bitweiser AND-Operator: &amp;'
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: ba17c9a633b7b18cad2881dfef90fde7c2074319
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446140"
---
# <a name="bitwise-and-operator-amp"></a>Bitweiser AND-Operator: &amp;

## <a name="syntax"></a>Syntax

```
expression & expression
```

## <a name="remarks"></a>Bemerkungen

Die Ausdrücke können andere und-Ausdrücke sein oder (unter Berücksichtigung der Typeinschränkungen, die unten genannt werden) Gleichheitsausdrücke, relationale Ausdrücke, additive Ausdrücke, multiplikative Ausdrücke, Zeiger-zu-Member-Ausdrücke, Umwandlungsausdrücke, unäre Ausdrücke, Postfix-Ausdrücke oder primäre Ausdrücke.

Der bitweise AND-Operator ( **&** ) vergleicht jedes Bit des ersten Operanden mit dem entsprechenden Bit des zweiten Operanden. Wenn beide Bits 1 sind, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 festgelegt.

Beide Operanden im bitweisen AND-Operator müssen vom Ganzzahltyp sein. Die üblichen arithmetischen Konvertierungen, die in [Standard Konvertierungen](standard-conversions.md)abgedeckt werden, werden auf die Operanden angewendet.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für &

Der **BITAND-** Operator ist die Text Entsprechung von **&** . Es gibt zwei Möglichkeiten, auf den **BITAND** -Operator in ihren Programmen zuzugreifen: Schließen Sie die Header Datei `iso646.h`ein, oder kompilieren Sie mit der Compileroption [/Za](../build/reference/za-ze-disable-language-extensions.md) (Spracherweiterungen deaktivieren).

## <a name="example"></a>Beispiel

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren zur Bitmanipulation](../c-language/c-bitwise-operators.md)