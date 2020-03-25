---
title: for-Anweisung (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: e3dfdb45bdf8a508eca9d29e90b3f7c05e7b147d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179912"
---
# <a name="for-statement-c"></a>for-Anweisung (C++)

Führt eine Anweisung wiederholt aus, bis die Bedingung false ergibt. Weitere Informationen zur Bereichs basierten for-Anweisung finden Sie unter [Range-based for-AnweisungC++()](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntax

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die **for** -Anweisung zum Erstellen von Schleifen, die eine angegebene Anzahl von Wiederholungen ausführen müssen.

Die **for** -Anweisung besteht aus drei optionalen teilen, wie in der folgenden Tabelle dargestellt.

### <a name="for-loop-elements"></a>for-Schleifenelemente

|Syntaxname|Ausführung bei|BESCHREIBUNG|
|-----------------|-------------------|-----------------|
|`init-expression`|Vor jedem anderen Element der **for** -Anweisung wird `init-expression` nur einmal ausgeführt. Das Steuerelement wird dann an `cond-expression` übergeben.|Wird häufig zum Initialisieren von Schleifenindizes verwendet. Es können Ausdrücke oder Deklarationen enthalten sein.|
|`cond-expression`|Vor der Ausführung jeder Iteration von `statement`, einschließlich der ersten Iteration. `statement` wird nur ausgeführt, wenn `cond-expression` den Wert „True“ (ungleich 0 (null)) annimmt.|Ein Ausdruck, der einen Ganzzahltyp oder einen Klassentyp ergibt, der über eine eindeutige Konvertierung in einen Ganzzahltyp verfügt. Wird normalerweise zum Testen von Beendigungskriterien für Schleifen verwendet.|
|`loop-expression`|Am Ende jeder Iteration von `statement`. Nachdem `loop-expression` ausgeführt wird, wird `cond-expression` ausgewertet.|Wird normalerweise zum Erhöhen von Schleifenindizes verwendet.|

Die folgenden Beispiele zeigen verschiedene Möglichkeiten, die **for** -Anweisung zu verwenden.

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
}
    // Output: 012
```

`init-expression` und `loop-expression` können mehrere durch Kommas getrennte Anweisungen enthalten. Beispiel:

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

Der `loop-expression` kann erweitert oder verringert werden oder in anderer Weise geändert werden.

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

Eine **for** -Schleife wird beendet, wenn eine [break](../cpp/break-statement-cpp.md)-, [Return](../cpp/return-statement-cpp.md)-oder [goto](../cpp/goto-statement-cpp.md) -Anweisung (an eine Anweisung mit Bezeichnung außerhalb der **for** -Schleife) innerhalb `statement` ausgeführt wird. Eine [Continue](../cpp/continue-statement-cpp.md) -Anweisung in einer **for** -Schleife beendet nur die aktuelle Iterations Anweisung.

Wenn `cond-expression` weggelassen wird, wird es als true angesehen, und die **for** -Schleife wird nicht ohne **Pause**, **Return**oder **goto** innerhalb `statement`beendet.

Obwohl die drei Felder der **for** -Anweisung normalerweise für die Initialisierung, das Testen auf Beendigung und das Inkrementieren verwendet werden, sind Sie nicht auf diese Verwendungszwecke beschränkt. Beispielsweise gibt der folgende Code die Zahlen 0 bis 4 aus. In diesem Fall handelt es sich bei `statement` um die null-Anweisung:

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

## <a name="for-loops-and-the-c-standard"></a>for-Schleifen und der C++-Standard

Der C++ Standard besagt, dass eine in einer **for** -Schleife deklarierte Variable außerhalb des Gültigkeits Bereichs liegt, wenn die **for** -Schleife beendet wird. Beispiel:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Standardmäßig bleibt unter [/Ze](../build/reference/za-ze-disable-language-extensions.md)eine in einer **for** -Schleife deklarierte Variable im Gültigkeitsbereich, bis der einschließende Bereich der **for** -Schleife beendet wird.

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) ermöglicht das Standardverhalten von in for-Schleifen deklarierten Variablen, ohne `/Za`angeben zu müssen.

Es ist auch möglich, die Bereichs Unterschiede der **for** -Schleife zum erneuten Deklarieren von Variablen unter `/Ze` wie folgt zu verwenden:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Dadurch wird das Standardverhalten einer Variablen, die in einer **for** -Schleife deklariert ist, genauer imitiert. Dies erfordert, dass in einer **for** -Schleife deklarierte Variablen außerhalb des Gültigkeits Bereichs liegen, nachdem die Schleife abgeschlossen wurde. Wenn eine Variable in einer **for** -Schleife deklariert wird, stuft der Compiler Sie intern auf eine lokale Variable im einschließenden Bereich der **for** -Schleife herauf, auch wenn bereits eine lokale Variable mit demselben Namen vorhanden ist.

## <a name="see-also"></a>Weitere Informationen

[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[while-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Bereichsbasiert für Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
