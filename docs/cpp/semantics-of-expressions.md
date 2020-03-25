---
title: Semantik von Ausdrücken
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: 5213fc7972f3a2590ceac5038a7b5e07495df594
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178848"
---
# <a name="semantics-of-expressions"></a>Semantik von Ausdrücken

Ausdrücke werden entsprechend der Rangfolge und Gruppierung ihrer Operatoren ausgewertet. ([Operator Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md) in [lexikalischen Konventionen](../cpp/lexical-conventions.md)zeigt die Beziehungen an C++ , die die Operatoren für Ausdrücke erzwingen.)

## <a name="order-of-evaluation"></a>Reihenfolge der Auswertung

Betrachten Sie dieses Beispiel:

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![Auswertungs Reihenfolge in einem Ausdruck](../cpp/media/vc38zv1.gif "Auswertungsreihenfolge in einem Ausdruck") <br/>
Ausdruck-Auswertungs Reihenfolge

Die Reihenfolge der Auswertung des in der obigen Abbildung dargestellten Ausdrucks wird durch die Reihenfolge und die Assoziativität der Operatoren bestimmt:

1. Multiplikation (*) weist die höchste Priorität in diesem Ausdruck auf. Daher wird der Teilausdruck `b * c` zuerst ausgewertet.

1. Addition (+) besitzt die zweithöchste Priorität, sodass `a` dem Produkt von `b` und `c` hinzugefügt wird.

1. Left Shift (< <) hat die niedrigste Rangfolge im Ausdruck, es gibt jedoch zwei vorkommen. Da der Left Shift-Operator von links nach rechts gruppiert, wird zuerst der linke und dann der rechte Teilausdruck ausgewertet.

Wenn Teilausdrücke mit Klammern gruppiert werden, werden die Rangfolge sowie die Reihenfolge der Auswertung des Ausdrucks geändert, wie in der folgenden Abbildung gezeigt.

![Auswertungs Reihenfolge des Ausdrucks mit Klammern](../cpp/media/vc38zv2.gif "Auswertungsreihenfolge eines Ausdrucks mit Klammern") <br/>
Ausdruck-Auswertungs Reihenfolge mit Klammern

Ausdrücke, wie in der Abbildung oben, werden ausschließlich für ihre Nebeneffekte ausgewertet – in diesem Fall, um Informationen zum Standardausgabegerät zu übertragen.

## <a name="notation-in-expressions"></a>Notation in Ausdrücken

Die Programmiersprache C++ gibt beim Angeben von Operanden bestimmte Kompatibilitäten an. In der folgenden Tabelle sind die Typen von Operanden aufgeführt, die für Operatoren zulässig sind, die Operanden vom *Typ Type benötigen.*

### <a name="operand-types-acceptable-to-operators"></a>Operandentypen, die für Operatoren zulässig sind

|Typ erwartet|Typen zulässig|
|-------------------|-------------------|
|*type*|`const`- *Typ*<br /> `volatile`- *Typ*<br /> *Typ*&<br /> `const` *Typ*&<br /> `volatile` *Typ*&<br /> `volatile const`- *Typ*<br /> `volatile const` *Typ*&|
|\* *eingeben*|\* *eingeben*<br /> `const` *Typ* \*<br /> `volatile` *Typ* \*<br /> `volatile const` *Typ* \*|
|`const`- *Typ*|*type*<br /> `const`- *Typ*<br />`const` *Typ*&|
|`volatile`- *Typ*|*type*<br /> `volatile`- *Typ*<br /> `volatile` *Typ*&|

Da die vorangehenden Regeln immer in Kombination verwendet werden können, kann ein const-Zeiger auf ein flüchtiges Objekt angegeben werden, wo ein Zeiger erwartet wird.

## <a name="ambiguous-expressions"></a>Mehrdeutige Ausdrücke

Bestimmte Ausdrücke sind mehrdeutig. Diese Ausdrücke treten am häufigsten auf, wenn der Wert eines Objekts mehrfach im selben Ausdruck geändert wird. Diese Ausdrücke basieren auf einer bestimmten Auswertungsreihenfolge, wenn sie von der Sprache nicht definiert wird. Betrachten Sie das folgenden Beispiel:

```
int i = 7;

func( i, ++i );
```

Die Programmiersprache C++ gewährleistet nicht die Reihenfolge, in der Argumente zu einem Funktionsaufruf ausgewertet werden. Daher könnte `func` im vorhergehenden Beispiel die Werte 7 und 8 oder 8 und 8 für die Parameter empfangen, je nachdem, ob die Parameter von links nach rechts oder von rechts nach links ausgewertet werden.

## <a name="c-sequence-points-microsoft-specific"></a>C++Sequenz Punkte (Microsoft-spezifisch)

Zwischen aufeinanderfolgenden "Sequenzpunkten" kann der Wert eines Objekts nur einmal durch einen Ausdruck geändert werden.

Die C++-Sprachendefinition gibt derzeit keine Sequenzpunkte an. Microsoft C++ verwendet dieselben Sequenzpunkte wie ANSI C für jeden beliebigen Ausdruck, der C-Operatoren einbezieht und nicht überladene Operatoren beinhaltet. Wenn Operatoren überladen werden, wird die Semantik von Operatorseqenzierung in Funktionsaufrufsequenzierung geändert. Microsoft C++ verwendet folgende Sequenzpunkte:

- Linker Operand des logischen AND-Operators (& &). Der linke Operand des logischen AND-Operators wird vollständig ausgewertet, und alle Nebeneffekte werden vor dem Fortsetzen abgeschlossen. Es gibt keine Garantie, dass der rechte Operand des logischen AND-Operators ausgewertet wird.

- Linker Operand des logischen OR-Operators (&#124;&#124;). Der linke Operand des logischen OR-Operators wird vollständig ausgewertet, und alle Nebeneffekte werden vor dem Fortsetzen abgeschlossen. Es gibt keine Garantie, dass der rechte Operand des logischen OR-Operators ausgewertet wird.

- Linker Operand des Komma-Operators. Der linke Operand des Komma-Operators wird vollständig ausgewertet, und alle Nebeneffekte werden vor dem Fortsetzen abgeschlossen. Beide Operanden des Komma-Operators werden immer ausgewertet.

- Funktionsaufrufoperator. Der Funktionsaufrufausdruck und alle Argumente für eine Funktion, einschließlich Standardargumente, werden ausgewertet und alle Nebeneffekte werden vor dem Eintritt in die Funktion abgeschlossen. Es gibt keine festgelegte Reihenfolge der Auswertung unter den Argumenten bzw. beim Funktionsaufrufausdruck.

- Der erste Operand des bedingten Operators. Der erste Operand des bedingten Operators wird vollständig ausgewertet, und alle Nebeneffekte werden vor dem Fortsetzen abgeschlossen.

- Das Ende eines vollständigen Initialisierungsausdrucks, wie das Ende einer Initialisierung in einer Deklarationsanweisung.

- Der Ausdruck in einer Ausdrucksanweisung. Ausdrucksanweisungen bestehen aus einem optionalen Ausdruck, dem ein Semikolon (;) folgt. Der Ausdruck wird vollständig für die Nebeneffekte ausgewertet.

- Der steuernde Ausdruck in einer Auswahlanweisung ("if" oder "switch"). Der Ausdruck wird vollständig ausgewertet, und alle Nebeneffekte werden abgeschlossen, bevor der von der Auswahl abhängige Code ausgeführt wird.

- Der steuernde Ausdruck einer while- oder do-Anweisung. Der Ausdruck wird vollständig ausgewertet, und alle Nebeneffekte werden abgeschlossen, bevor eine beliebige Anweisung in der nächsten Iteration der while- oder do-Schleife ausgeführt wird.

- Jede der drei Ausdrücke einer for-Anweisung. Jeder Ausdruck wird vollständig ausgewertet, und alle Nebeneffekte werden geschlossen, bevor zum nächsten Ausdruck gewechselt wird.

- Der Ausdruck in einer return-Anweisung. Der Ausdruck wird vollständig ausgewertet, und alle Nebeneffekte werden abgeschlossen, bevor die Steuerung an die aufrufende Funktion zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke](../cpp/expressions-cpp.md)
