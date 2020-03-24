---
title: 'Operator für logisches ODER: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 94b2bc024dd7223ac7adacc72924f5ee289bab37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178079"
---
# <a name="logical-or-operator-"></a>Operator für logisches ODER: ||

## <a name="syntax"></a>Syntax

> *logischer or-Ausdruck* **||** Ausdruck "logischer Ausdruck" *und* "Ausdruck"

## <a name="remarks"></a>Bemerkungen

Der logische OR-Operator ( **||** ) gibt den booleschen Wert true zurück, wenn einer der Operanden oder beide Operanden true ist, andernfalls wird false zurückgegeben. Die Operanden werden vor der Auswertung implizit in den Typ **bool** konvertiert, und das Ergebnis ist vom Typ **bool**. Das logische OR weist eine Assoziativität von links nach rechts auf.

Die Operanden für den logischen OR-Operator müssen nicht vom gleichen Typ sein, aber sie müssen Ganzzahltypen oder Zeigertypen sein. Die Operanden sind im Allgemeinen relationale oder Gleichheitsausdrücke.

Der erste Operand wird vollständig ausgewertet und alle Nebeneffekte werden abgeschlossen, bevor die Auswertung des logischen OR-Ausdrucks fortgesetzt wird.

Der zweite Operand wird nur ausgewertet, wenn der erste Operand als false (0) ausgewertet wird. Diese Auswertung eliminiert die unnötige Auswertung des zweiten Operanden, wenn der logische OR-Ausdruck TRUE ist.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Im Beispiel oben, wenn `x` entweder gleich `w`, `y` oder `z` ist, wird das zweite Argument für die `printf`-Funktion mit TRUE ausgewertet, und der Wert 1 wird ausgegeben. Andernfalls wird dies mit "false" ausgewertet, und der Wert 0 (null) wird ausgegeben. Sobald eine der Bedingungen mit dem Ergebnis "true" ausgewertet wird, wird die Auswertung beendet.

## <a name="operator-keyword-for-124124"></a>Operator Schlüsselwort für&#124;&#124;

Der **or** -Operator ist die Text Entsprechung von **||** . Es gibt zwei Möglichkeiten, auf den **or** -Operator in ihren Programmen zuzugreifen: Schließen Sie die Header Datei \<iso646. h > ein, oder kompilieren Sie mit der [/Za](../build/reference/za-ze-disable-language-extensions.md) -Compileroption (Spracherweiterungen deaktivieren).

## <a name="example"></a>Beispiel

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Weitere Informationen

[C++Rangfolge und Assoziativität integrierter Operatoren](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren (logisch)](../c-language/c-logical-operators.md)
