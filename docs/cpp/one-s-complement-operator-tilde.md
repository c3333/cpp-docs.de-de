---
title: 'Ein&#39;-e-Komplement Operator: ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177715"
---
# <a name="one39s-complement-operator-"></a>Ein&#39;-e-Komplement Operator: ~

## <a name="syntax"></a>Syntax

```
~ cast-expression
```

## <a name="remarks"></a>Bemerkungen

Der Einerkomplementoperator (`~`), der manchmal als "bitweiser Komplementoperator" bezeichnet wird, ergibt eine bitweise Einerkomplement seines Operanden. Das bedeutet, dass jedes Bit, das 1 im Operanden ist, 0 im Ergebnis ist. Umgekehrt ist jedes Bit, das 0 im Operanden ist, im Ergebnis 1. Der Operand für den Einerkomplementoperator muss ein ganzzahliger Typ sein.

## <a name="operator-keyword-for-"></a>Operator-Schlüsselwort für ~

Der **compl** -Operator ist die Text Entsprechung von `~`. Es gibt zwei Möglichkeiten, auf den **compl** -Operator in ihren Programmen zuzugreifen: Schließen Sie die Header Datei `iso646.h`ein, oder kompilieren Sie mit [/Za](../build/reference/za-ze-disable-language-extensions.md).

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

Ganzzahlige Erweiterung wird für ganzzahlige Operanden durchgeführt, und der resultierende Typ ist der Typ, auf den der Operand erweitert wird. Weitere Informationen zur Ausführung der herauf Stufung finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md)
