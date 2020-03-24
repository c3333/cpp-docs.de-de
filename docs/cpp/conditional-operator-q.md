---
title: 'Bedingter Operator: &quest;:'
ms.date: 11/04/2016
f1_keywords:
- '?:'
- '?'
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
ms.openlocfilehash: 8c00db06ed5c0347cb9c720e35bd3e517df2a13c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189577"
---
# <a name="conditional-operator-quest-"></a>Bedingter Operator: &quest;:

## <a name="syntax"></a>Syntax

```
expression ? expression : expression
```

## <a name="remarks"></a>Bemerkungen

Der bedingte Operator ( **?:** ) ist ein ternärer Operator (er benötigt drei Operanden). Der bedingte Operator funktioniert wie folgt:

- Der erste Operand wird implizit in einen **booleschen**Wert konvertiert. Er wird ausgewertet, und alle Nebeneffekte werden vor dem nächsten Schritt abgeschlossen.

- Wenn der erste Operand als **true** (1) ausgewertet wird, wird der zweite Operand ausgewertet.

- Wenn der erste Operand als **false** (0) ausgewertet wird, wird der dritte Operand ausgewertet.

Das Ergebnis des bedingten Operators ist das Ergebnis des ausgewerteten Operanden – der zweite oder dritte. Nur einer der letzten zwei Operanden wird in einem bedingten Ausdruck ausgewertet.

Bedingte Ausdrücke besitzen Assoziativität von rechts nach links. Der erste Operand muss ein ganzzahliger Typ oder ein Zeigertyp sein. Die folgenden Regeln gelten für die zweiten und dritten Operanden:

- Wenn beide Operanden vom selben Typ sind, ist das Ergebnis von diesem Typ.

- Wenn beide Operanden arithmetische oder Enumerationstypen sind, werden die üblichen arithmetischen Konvertierungen (in [Standard Konvertierungen](standard-conversions.md)abgedeckt) ausgeführt, um Sie in einen gemeinsamen Typ zu konvertieren.

- Wenn beide Operanden Zeigertypen sind, oder wenn einer ein Zeigertyp und der andere ein konstanter Ausdruck ist, der 0 ergibt, werden Zeigerkonvertierungen ausgeführt, um sie in einen gemeinsamen Typ zu konvertieren.

- Wenn beide Operanden Verweistypen sind, werden Verweiskonvertierungen ausgeführt, um sie in einen gemeinsamen Typ zu konvertieren.

- Wenn beide Operanden vom Typ „void“ sind, ist der gemeinsame Typ „void“.

- Wenn beide Operanden vom selben benutzerdefinierten Typ sind, ist der gemeinsame Typ dieser Typ.

- Wenn die Operanden unterschiedliche Typen aufweisen und mindestens einer der Operanden den benutzerdefinierten Typ aufweist, werden die Sprachregeln zum Bestimmen des allgemeinen Typs verwendet. (Siehe obige Warnung.)

Alle Kombinationen von zweiten und dritten Operanden, die nicht in der vorangehenden Liste enthalten sind, sind ungültig. Der Ergebnistyp ist der gemeinsame Typ, und es ist ein L-Wert, wenn die zweiten und dritten Operanden vom selben Typ und beide L-Werte sind.

> [!WARNING]
>  Wenn die Typen der zweiten und dritten Operanden nicht identisch sind, werden komplexe Typkonvertierungsregeln gemäß C++-Standard aufgerufen. Diese Konvertierungen können zu unerwartetem Verhalten führen, einschließlich der Erstellung und Zerstörung von temporären Objekten. Aus diesem Grund empfehlen wir dringend, dass Sie entweder (1) keine benutzerdefinierten Typen als Operanden mit dem bedingten Operator verwenden oder (2) explizit jeden Operanden in einen gemeinsamen Typ umwandeln, wenn Sie benutzerdefinierte Typen verwenden.

## <a name="example"></a>Beispiel

```cpp
// expre_Expressions_with_the_Conditional_Operator.cpp
// compile with: /EHsc
// Demonstrate conditional operator
#include <iostream>
using namespace std;
int main() {
   int i = 1, j = 2;
   cout << ( i > j ? i : j ) << " is greater." << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Bedingter Ausdrucksoperator](../c-language/conditional-expression-operator.md)
