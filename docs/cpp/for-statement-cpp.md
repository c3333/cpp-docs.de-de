---
title: for-Anweisung (C++)
description: Verweis auf die Standard-C++-Anweisung für die Anweisung in Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375384"
---
# <a name="for-statement-c"></a>for-Anweisung (C++)

Führt eine Anweisung wiederholt aus, bis die Bedingung false ergibt. Informationen zur bereichsbasierten For-Anweisung finden Sie unter [Bereichsbasiert für Anweisung (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntax

> **`for (`***init-expression* **`;`** *cond-expression-Loop-Expression* **`;`** *loop-expression***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_Anweisung_**`;`**

## <a name="remarks"></a>Bemerkungen

Verwenden **for** Sie die for-Anweisung, um Schleifen zu erstellen, die eine bestimmte Anzahl von Malen ausführen müssen.

Die **for-Anweisung** besteht aus drei optionalen Teilen, wie in der folgenden Tabelle dargestellt.

### <a name="for-loop-elements"></a>for-Schleifenelemente

|Syntaxname|Ausführung bei|BESCHREIBUNG|
|-----------------|-------------------|-----------------|
|`init-expression`|Vor einem anderen Element der `init-expression` **for-Anweisung** wird nur einmal ausgeführt. Das Steuerelement wird dann an `cond-expression` übergeben.|Wird häufig zum Initialisieren von Schleifenindizes verwendet. Es können Ausdrücke oder Deklarationen enthalten sein.|
|`cond-expression`|Vor der Ausführung jeder Iteration von `statement`, einschließlich der ersten Iteration. `statement` wird nur ausgeführt, wenn `cond-expression` den Wert „True“ (ungleich 0 (null)) annimmt.|Ein Ausdruck, der einen Ganzzahltyp oder einen Klassentyp ergibt, der über eine eindeutige Konvertierung in einen Ganzzahltyp verfügt. Wird normalerweise zum Testen von Beendigungskriterien für Schleifen verwendet.|
|`loop-expression`|Am Ende jeder Iteration von `statement`. Nachdem `loop-expression` ausgeführt wird, wird `cond-expression` ausgewertet.|Wird normalerweise zum Erhöhen von Schleifenindizes verwendet.|

Die folgenden Beispiele zeigen verschiedene **for** Möglichkeiten zur Verwendung der for-Anweisung.

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

Eine **for-Schleife** wird beendet, wenn eine [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md)oder [goto](../cpp/goto-statement-cpp.md) `statement` (zu einer beschrifteten Anweisung außerhalb der **for-Schleife)** innerhalb ausgeführt wird. Eine [continue-Anweisung](../cpp/continue-statement-cpp.md) in einer **for-Schleife** beendet nur die aktuelle Iteration.

Wenn `cond-expression` weggelassen wird, `true`wird sie berücksichtigt, und die **for-Schleife** wird nicht `statement`ohne **Unterbrechung,** **Rückgabe**oder **goto** in beendet.

Obwohl die drei Felder der **for-Anweisung** normalerweise für Initialisierung, Beenden und Inkrementieren verwendet werden, sind sie nicht auf diese Verwendungen beschränkt. Beispielsweise gibt der folgende Code die Zahlen 0 bis 4 aus. In diesem Fall handelt es sich bei `statement` um die null-Anweisung:

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

Der C++-Standard besagt, dass eine Variable, die in einer **for-Schleife** deklariert wurde, nach dem Ende der **for-Schleife** aus dem Gültigkeitsbereich herausgehen soll. Beispiel:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Standardmäßig bleibt unter [/Ze](../build/reference/za-ze-disable-language-extensions.md)eine variable Variable, die in einer **for-Schleife** deklariert wird, im Gültigkeitsbereich, bis der einschließende Bereich der **for-Schleife** endet.

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) aktiviert das Standardverhalten von Variablen, die `/Za`für Schleifen deklariert wurden, ohne angeben zu müssen.

Es ist auch möglich, die Scoping-Unterschiede der **for-Schleife** zu verwenden, um Variablen unter `/Ze` wie folgt neu zu deklarieren:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Dieses Verhalten imitiert das Standardverhalten einer Variablen, die in einer **for-Schleife** deklariert wurde, die Variablen, die in einer **for-Schleife** deklariert wurden, nach Abschluss der Schleife aus dem Gültigkeitsbereich herauslaufen muss. Wenn eine Variable in einer **for-Schleife** deklariert wird, wird sie intern vom Compiler zu einer lokalen Variable im einschließenden Bereich der **for-Schleife** heraufbeauft. Es wird gefördert, auch wenn es bereits eine lokale Variable mit dem gleichen Namen gibt.

## <a name="see-also"></a>Siehe auch

[Iterationsanweisungen](../cpp/iteration-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[while-Anweisung (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while-Anweisung (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Bereichsbasiert für Anweisung (C++)](../cpp/range-based-for-statement-cpp.md)
