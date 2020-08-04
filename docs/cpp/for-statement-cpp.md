---
title: for-Anweisung (C++)
description: Verweis auf die C++ for-Standard Anweisung in Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 07/31/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: b32a50e376113f9f9d550d4984d05fc8c675f14d
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520848"
---
# <a name="for-statement-c"></a>`for`Anweisung (C++)

Führt eine Anweisung wiederholt aus, bis die Bedingung false ergibt. Weitere Informationen zur Bereichs basierten **`for`** Anweisung finden Sie unter [Bereichs basierte `for` Anweisung (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntax

> **`for (`** *`init-expression`* **`;`** *`cond-expression`* **`;`** *`loop-expression`* **`)`**\
> &emsp;*`statement`*

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die- **`for`** Anweisung, um Schleifen zu erstellen, die eine angegebene Anzahl von Wiederholungen ausführen müssen.

Die- **`for`** Anweisung besteht aus drei optionalen teilen, wie in der folgenden Tabelle dargestellt.

### <a name="for-loop-elements"></a>for-Schleifen Elemente

| Syntax Name | Bei Ausführung | Beschreibung |
|--|--|--|
| *`init-expression`* | Vor jedem anderen Element der- **`for`** Anweisung *`init-expression`* wird nur ein Mal ausgeführt. Dann übergibt das Steuerelement an *`cond-expression`* . | Wird häufig zum Initialisieren von Schleifenindizes verwendet. Es können Ausdrücke oder Deklarationen enthalten sein. |
| *`cond-expression`* | Vor der Ausführung jeder Iterationen von *`statement`* , einschließlich der ersten Iterationen. *`statement`* wird nur ausgeführt *`cond-expression`* , wenn als true (ungleich null) ausgewertet wird. | Ein Ausdruck, der einen Ganzzahltyp oder einen Klassentyp ergibt, der über eine eindeutige Konvertierung in einen Ganzzahltyp verfügt. Wird normalerweise zum Testen von Beendigungskriterien für Schleifen verwendet. |
| *`loop-expression`* | Am Ende jeder Iterationen von *`statement`* . Nachdem *`loop-expression`* ausgeführt wurde, *`cond-expression`* wird ausgewertet. | Wird normalerweise zum Erhöhen von Schleifenindizes verwendet. |

Die folgenden Beispiele zeigen verschiedene Möglichkeiten, die- **`for`** Anweisung zu verwenden.

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
    // Output: 01
}
```

*`init-expression`* und *`loop-expression`* können mehrere-Anweisungen enthalten, die durch Kommas getrennt sind. Zum Beispiel:

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

*`loop-expression`* kann inkrementiert oder dekrementiert oder auf andere Weise geändert werden.

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

Eine- **`for`** Schleife wird beendet [`break`](../cpp/break-statement-cpp.md) , wenn eine, [Return](../cpp/return-statement-cpp.md)oder [`goto`](../cpp/goto-statement-cpp.md) (an eine Anweisung mit Bezeichnung außerhalb der- **`for`** Schleife) innerhalb von *`statement`* ausgeführt wird. Eine- [`continue`](../cpp/continue-statement-cpp.md) Anweisung in einer- **`for`** Schleife beendet nur die aktuelle Iterations-.

Wenn *`cond-expression`* weggelassen wird, wird Sie berücksichtigt **`true`** , und die- **`for`** Schleife wird nicht ohne **`break`** , **`return`** oder **`goto`** in beendet *`statement`* .

Obwohl die drei Felder der- **`for`** Anweisung normalerweise für die Initialisierung, das Testen auf Beendigung und das Inkrementieren verwendet werden, sind Sie nicht auf diese Verwendungszwecke beschränkt. Beispielsweise gibt der folgende Code die Zahlen 0 bis 4 aus. In diesem Fall *`statement`* ist die NULL-Anweisung:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>`for`Schleifen und der C++-Standard

Der C++-Standard besagt, dass eine in einer-Schleife deklarierte Variable außerhalb des Gültigkeits Bereichs liegt, **`for`** Wenn die **`for`** Schleife beendet wird. Zum Beispiel:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Standardmäßig bleibt unter [/Ze](../build/reference/za-ze-disable-language-extensions.md)eine in einer-Schleife deklarierte Variable im Gültigkeits **`for`** Bereich, bis der **`for`** umschließende Bereich der Schleife endet.

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) ermöglicht das Standardverhalten von Variablen, die in for-Schleifen deklariert sind, ohne dass Sie angeben müssen `/Za` .

Es ist auch möglich, die Bereichs Unterschiede der **`for`** Schleife zum erneuten Deklarieren von Variablen unter `/Ze` wie folgt zu verwenden:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Dieses Verhalten imitiert das Standardverhalten einer Variablen, die in einer-Schleife deklariert ist **`for`** , genauer, was erfordert, dass in einer-Schleife deklarierte Variablen außerhalb des Gültigkeits Bereichs liegen, **`for`** nachdem die Schleife abgeschlossen wurde. Wenn eine Variable in einer **`for`** -Schleife deklariert wird, stuft der Compiler Sie intern auf eine lokale Variable im **`for`** einschließenden Bereich der Schleife herauf. Sie wird auch dann herauf gestuft, wenn bereits eine lokale Variable mit demselben Namen vorhanden ist.

## <a name="see-also"></a>Siehe auch

[Iterations Anweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[While-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[Do-While-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Range-based for-Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
