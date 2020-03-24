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
ms.openlocfilehash: 32c210961c4966bb7b2cbcc597bd3c99f0d6ed24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177663"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>Inkrementierungs- und Dekrementierungsoperatoren in Präfixnotation: ++ und --

## <a name="syntax"></a>Syntax

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Bemerkungen

Der Präfix Inkrementoperator ( **++** ) fügt einen dem Operanden hinzu. dieser inkrementierte Wert ist das Ergebnis des Ausdrucks. Der Operand muss ein l-Wert sein, der nicht vom Typ " **Konstanten**" ist. Das Ergebnis ist ein L-Wert des gleichen Typs wie der Operand.

Der Präfix-Dekrementoperator ( **--** ) entspricht dem Präfix Inkrementoperator, mit dem Unterschied, dass der Operand um eins verringert wird und das Ergebnis dieser dekrementierte Wert ist.

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): der Operand eines Inkrement-oder Dekrementoperators darf nicht den Typ " **bool**" aufweisen.

Sowohl Präfix- als auch Postfixinkrement und Dekrementoperatoren beeinflussen ihre Operanden. Der wesentliche Unterschied zwischen ihnen besteht in der Reihenfolge von Inkrement und Dekrement bei der Auswertung eines Ausdrucks. (Weitere Informationen finden Sie unter [postfix-Inkrement-und Dekrementoperatoren](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md).) Im Präfix Formular findet das Inkrement oder Dekrement statt, bevor der Wert in der Ausdrucks Auswertung verwendet wird, daher unterscheidet sich der Wert des Ausdrucks vom Wert des Operanden. In der Postfix-Form findet das Inkrement oder Dekrement statt, nachdem der Wert in der Ausdrucksauswertung verwendet wird, daher ist der Wert des Ausdrucks der gleiche wie der Wert des Operanden. Zum Beispiel gibt das folgende Programm "`++i = 6`" aus:

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

Da Inkrement-und Dekrementoperatoren Nebeneffekte haben, kann das Verwenden von Ausdrücken mit Inkrement-oder Dekrementoperatoren in einem [Präprozessormakro](../preprocessor/macros-c-cpp.md) unerwünschte Ergebnisse aufweisen. Betrachten Sie dieses Beispiel:

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
>  C++-Inlinefunktionen sind in vielen Fällen Makros vorzuziehen, da diese Nebeneffekte, wie die hier beschriebenen, ausschließen und der Programmiersprache die weitere Ausführung vollständigerer Typüberprüfung ermöglichen.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Inkrementierungs- und Dekrementierungsoperatoren in Präfixnotation](../c-language/prefix-increment-and-decrement-operators.md)
