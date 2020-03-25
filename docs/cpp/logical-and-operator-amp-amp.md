---
title: 'Logischer and-Operator: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: b21d91009c455b67af6fae88fceafeeaf8043301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179431"
---
# <a name="logical-and-operator-ampamp"></a>Logischer and-Operator: &amp;&amp;

## <a name="syntax"></a>Syntax

```
expression && expression
```

## <a name="remarks"></a>Hinweise

Der logische And-Operator ( **&&** ) gibt den booleschen Wert true zurück, wenn beide Operanden true sind, andernfalls wird false zurückgegeben. Die Operanden werden vor der Auswertung implizit in den Typ **bool** konvertiert, und das Ergebnis ist vom Typ **bool**. Das logische AND weist eine Assoziativität von links nach rechts auf.

Die Operanden für den logischen AND-Operator müssen nicht vom gleichen Typ sein, aber sie müssen Ganzzahltypen oder Zeigertypen sein. Die Operanden sind im Allgemeinen relationale oder Gleichheitsausdrücke.

Der erste Operand wird vollständig ausgewertet und alle Nebeneffekte werden abgeschlossen, bevor die Auswertung des logischen AND-Ausdrucks fortgesetzt wird.

Der zweite Operand wird nur dann ausgewertet, wenn der erste Operand als true (ungleich Null) ausgewertet wird. Diese Auswertung eliminiert die unnötige Auswertung des zweiten Operanden, wenn der Ausdruck der logischen AND-Operation gleich FALSE ist. Mithilfe dieser Kurzschlussauswertung können Sie Dereferenzierungen durch NULL-Zeiger verhindern, wie im folgenden Beispiel gezeigt:

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Wenn `pch` null (0) ist, wird die rechte Seite des Ausdrucks niemals ausgewertet. Daher ist die Zuweisung durch einen NULL-Zeiger unmöglich.

## <a name="operator-keyword-for-"></a>Operator Schlüsselwort für & &

Der **and-** Operator ist die Text Entsprechung von **&&** . Es gibt zwei Möglichkeiten, auf den **and-** Operator in ihren Programmen zuzugreifen: Schließen Sie die Header Datei `iso646.h`ein, oder kompilieren Sie mit der Compileroption [/Za](../build/reference/za-ze-disable-language-extensions.md) (Spracherweiterungen deaktivieren).

## <a name="example"></a>Beispiel

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Siehe auch

[C++Rangfolge und Assoziativität integrierter Operatoren](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C-Operatoren (logisch)](../c-language/c-logical-operators.md)
