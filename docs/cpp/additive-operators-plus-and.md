---
title: 'Additive Operatoren: + und -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: 739132ce1889b7e73b7ae19f5072a1dfec9c066d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181667"
---
# <a name="additive-operators--and--"></a>Additive Operatoren: + und -

## <a name="syntax"></a>Syntax

```
expression + expression
expression - expression
```

## <a name="remarks"></a>Bemerkungen

Die additiven Operatoren sind:

- Addition ( **+** )

- Subtraktion ( **-** )

Diese binären Operatoren weisen eine Assoziativität von links nach rechts auf.

Die additiven Operatoren nehmen Operanden der arithmetischen Operatoren oder Zeigertypen. Das Ergebnis des Additions Operators ( **+** ) ist die Summe der Operanden. Das Ergebnis des Subtraktions Operators ( **-** ) ist der Unterschied zwischen den Operanden. Wenn einer oder beide der Operanden Zeiger sind, müssen sie Zeiger auf Objekte, nicht auf Funktionen sein. Wenn beide Operanden Zeiger sind, sind die Ergebnisse nicht aussagekräftig, wenn nicht beide Zeiger auf Objekte im selben Array verweisen.

Additive Operatoren nehmen Operanden *arithmetischer* *, ganzzahliger und* *skalarer* Typen auf. Diese sind in der folgenden Tabelle definiert.

### <a name="types-used-with-additive-operators"></a>Mit additiven Operatoren verwendete Typen

|type|Bedeutung|
|----------|-------------|
|*Arithmetisch*|Ganzzahlige und nicht verankerte Typen werden kollektiv als "arithmetische" Typen bezeichnet.|
|*ganzzahligen*|Die Typen "char" und "int" in sämtlichen Größen ("long", "short") und Enumerationen sind ganzzahlige Typen.|
|*skalare*|Skalare Operanden sind entweder arithmetische oder Zeiger-Operanden.|

Die gültigen Kombinationen für diese Operatoren sind:

*arithmetische* + *Arithmetik*

*Skalar* + *integral* Ganzzahl

*integral* ganzzahliger + *Skalar*

*arithmetische* - *Arithmetik*

*Skalar* - *Skalarwert*

Beachten Sie, dass Addition und Subtraktion keine äquivalenten Vorgänge sind.

Wenn beide Operanden einen arithmetischen Typ haben, werden die in [Standard Konvertierungen](standard-conversions.md) behandelten Konvertierungen auf die Operanden angewendet, und das Ergebnis ist vom konvertierten Typ.

## <a name="example"></a>Beispiel

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>Zeigeraddition

Wenn einer der Operanden in einer Addition ein Zeiger auf ein Array von Objekten ist, muss der andere einen ganzzahligen Typ besitzen. Das Ergebnis ist ein Zeiger, der vom selben Typ wie der ursprüngliche Zeiger ist und auf ein anderes Arrayelement zeigt. Das folgende Codefragment veranschaulicht dieses Konzept:

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

Obwohl der Ganzzahlwert 1 zu `pIntArray` addiert wird, bedeutet dies nicht "1 zur Adresse addieren", sondern vielmehr "den Zeiger auf das nächste Objekt im Array richten", das 2 Bytes weiter ist (oder `sizeof( int )`).

> [!NOTE]
>  Code in Form von `pIntArray = pIntArray + 1` ist in C++-Programmen selten. Um ein Inkrement auszuführen, werden diese Formen bevorzugt: `pIntArray++` oder `pIntArray += 1`.

## <a name="pointer-subtraction"></a>Zeigersubtraktion

Wenn beide Operanden Zeiger sind, ist das Ergebnis der Subtraktion die Differenz (in Arrayelementen) zwischen den Operanden. Der Subtraktions Ausdruck ergibt ein ganzzahliges Ergebnis mit Vorzeichen vom Typ `ptrdiff_t` (definiert in der standardmäßigen Includedatei \<STDDEF. h >).

Einer der Operanden kann vom ganzzahligen Typ sein, solange er der zweite Operand ist. Das Ergebnis der Subtraktion ist vom selben Datentyp wie der ursprüngliche Zeiger. Der Wert der Subtraktion ist ein Zeiger auf das Array Element (*n* - *i*). dabei ist *n* das Element, auf das der ursprüngliche Zeiger zeigt, und *Ich bin* der ganzzahlige Wert des zweiten Operanden.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren (additiv)](../c-language/c-additive-operators.md)
