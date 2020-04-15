---
title: 'Inkrementierungs- und Dekrementierungsoperatoren in Präfixnotation: ++ und --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: ce066a3349d56b278739f586fe851b020da78885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366222"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Inkrementierungs- und Dekrementierungsoperatoren in Präfixnotation: ++ und --

## <a name="syntax"></a>Syntax

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Bemerkungen

Der Präfixinkrementoperator (**++**) fügt einen zu seinem Operanden hinzu. Dieser inkrementierte Wert ist das Ergebnis des Ausdrucks. Der Operand muss ein l-Wert und nicht vom Typ **const**sein. Das Ergebnis ist ein L-Wert des gleichen Typs wie der Operand.

Der Präfixdekremierungsoperator (**--**) entspricht dem Präfixinkrementoperator, mit der Ausnahme, dass der Operand um eins dekrementiert wird und das Ergebnis dieser dekrementierte Wert ist.

**Visual Studio 2017 Version 15.3 und höher** (verfügbar mit [/std:c++17](../build/reference/std-specify-language-standard-version.md)): Der Operand eines Inkrement- oder Dekrementoperators darf nicht vom Typ **bool**sein.

Sowohl Präfix- als auch Postfixinkrement und Dekrementoperatoren beeinflussen ihre Operanden. Der wesentliche Unterschied zwischen ihnen besteht in der Reihenfolge von Inkrement und Dekrement bei der Auswertung eines Ausdrucks. (Weitere Informationen finden Sie unter [Postfix-Inkrement- und Dekrement-Operatoren](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Im Präfixformular findet das Inkrement oder die Dekrementierung statt, bevor der Wert in der Ausdrucksauswertung verwendet wird, sodass sich der Wert des Ausdrucks vom Wert des Operanden unterscheidet. In der Postfix-Form findet das Inkrement oder Dekrement statt, nachdem der Wert in der Ausdrucksauswertung verwendet wird, daher ist der Wert des Ausdrucks der gleiche wie der Wert des Operanden. Zum Beispiel gibt das folgende Programm "`++i = 6`" aus:

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

Ein Operand vom Typ "Ganzzahl" oder "Gleitkomma" wird durch den ganzzahligen Wert 1 inkrementiert oder dekrementiert. Der Ergebnistyp entspricht dem Operandentyp. Ein Operand vom Zeigertyp wird um die Größe des von ihm adressierten Objekts inkrementiert oder dekrementiert. Ein inkrementierter Zeiger verweist auf das nächste Objekt. Ein dekrementierter Zeiger verweist auf das vorherige Objekt.

Da Inkrement- und Dekrementoperatoren Nebenwirkungen haben, kann die Verwendung von Ausdrücken mit Inkrement- oder Dekrementoperatoren in einem [Präprozessormakro](../preprocessor/macros-c-cpp.md) unerwünschte Ergebnisse haben. Betrachten Sie dieses Beispiel:

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

Das Makro wird wie folgt erweitert:

```cpp
k = ((++i)<(j))?(j):(++i);
```

Wenn `i` größer oder gleich `j` oder um 1 kleiner als `j` ist, wird es zweimal inkrementiert.

> [!NOTE]
> C++-Inlinefunktionen sind in vielen Fällen Makros vorzuziehen, da diese Nebeneffekte, wie die hier beschriebenen, ausschließen und der Programmiersprache die weitere Ausführung vollständigerer Typüberprüfung ermöglichen.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Inkrementierungs- und Dekrementierungsoperatoren in Präfixnotation](../c-language/prefix-increment-and-decrement-operators.md)
