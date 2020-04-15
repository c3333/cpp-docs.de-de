---
title: Multiplikationsoperatoren und der Modulus-Operator
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: 791f18793b49f7d3a986c3271fddef3acef33062
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367928"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Multiplikationsoperatoren und der Modulus-Operator

## <a name="syntax"></a>Syntax

```
expression * expression
expression / expression
expression % expression
```

## <a name="remarks"></a>Bemerkungen

Die multiplikativen Operatoren sind:

- Multiplikation<strong>\*</strong>( )

- Division**/**( )

- Modul (Rest aus der**%** Teilung) ( )

Diese binären Operatoren weisen eine Assoziativität von links nach rechts auf.

Die Multiplikationsoperatoren akzeptieren Operanden arithmetischer Typen. Der Moduloperator**%**( ) hat eine strengere Anforderung, dass seine Operanden vom integralen Typ sein müssen. (Um den Rest einer Gleitkomma-Division zu erhalten, verwenden Sie die Laufzeitfunktion, [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Die in [Standardkonvertierungen abgedeckten](standard-conversions.md) Konvertierungen werden auf die Operanden angewendet, und das Ergebnis ist der konvertierte Typ.

Der Multiplikationsoperator ergibt das Ergebnis der Multiplikation des ersten Operanden mit dem zweiten.

Der Divisionsoperator ergibt das Ergebnis der Division des ersten Operanden durch den zweiten.

Der Moduloperator ergibt den Rest durch den folgenden Ausdruck, wobei *e1* der erste Operand und *e2* der \* zweite ist: *e1* - (*e1* / *e2*) *e2*, wobei beide Operanden integraler Typ sind.

Division durch 0 (null) entweder in einer Division oder in einem Modulo-Ausdruck ist nicht definiert und verursacht einen Laufzeitfehler. Daher generieren die folgenden Begriffe nicht definierte, fehlerhafte Resultate:

```cpp
i % 0
f / 0.0
```

Wenn beide Operanden in einer Multiplikation, Division einer einem Modulo-Ausdruck dasselbe Vorzeichen haben, ist das Ergebnis positiv. Andernfalls ist das Ergebnis negativ. Das Ergebnis des Zeichens eines Modulvorgangs ist implementierungsdefiniert.

> [!NOTE]
> Da Konvertierungen, die von den Multiplikationsoperatoren ausgeführt werden, keine Überlauf- oder Unterlaufbedingungen vorsehen, gehen Informationen möglicherweise verloren, wenn das Ergebnis eines Multiplikationsvorgangs nach der Konvertierung nicht im Typ der Operanden dargestellt werden kann.

**Microsoft Specific**

In Microsoft C++ ist das Ergebnis eines Modulo-Ausdrucks immer dasselbe wie das Vorzeichen des ersten Operanden.

**END Microsoft Spezifisch**

Wenn die berechnete Division von zwei ganzen Zahlen ungenau ist und nur ein Operand negativ ist, ist das Ergebnis der Betrags (Wert ohne Vorzeichen) der größten Ganzzahl, die kleiner ist als der exakte Wert, den die Division ergeben würde. Der berechnete Wert von -11 / 3 ist beispielsweise -3.666666666. Das Ergebnis dieser integralen Teilung ist -3.

Die Beziehung zwischen den multiplikativen Operatoren wird durch \* die Identität (*e1* / *e2*) *e2* + *e1* % *e2* == *e1*angegeben.

## <a name="example"></a>Beispiel

Das folgende Programm demonstriert die multiplikativen Operatoren. Beachten Sie, dass `10 / 3` beide Operanden von explizit in den Typ **float** umgecastet werden müssen, um das Abschneiden zu vermeiden, sodass beide Operanden vom Typ **float** vor der Division sind.

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Multiplikationsoperatoren](../c-language/c-multiplicative-operators.md)
