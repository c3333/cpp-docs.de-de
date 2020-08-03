---
title: Argumente
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e1c88034044c74a542384873454f993b6bce3244
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232663"
---
# <a name="arguments"></a>Argumente

Die Argumente in einem Funktionsaufruf haben folgendes Format:

> *Ausdruck* **(** *Ausdrucksliste*<SUB>opt</SUB> **)**  /* Funktionsaufruf */

In einem Funktionsaufruf ist *expression-list* eine Liste von Ausdrücken (durch Kommas getrennt). Die Werte dieser letzten Ausdrücke sind die Argumente, die an die Funktion übergeben werden. Wenn die Funktion keine Argumente akzeptiert, sollte die *Ausdrucksliste* das Schlüsselwort **`void`** enthalten.

Ein Argument kann jeder Wert mit grundlegendem, Struktur-, Union- oder Zeigertyp sein. Alle Argumente werden durch einen Wert übergeben. Dies bedeutet, dass eine Kopie des Arguments den entsprechenden Parameter zugewiesen wird. Die Funktion kennt die tatsächliche Speicheradresse des übergebenen Arguments nicht. Die Funktion verwendet diese Kopie, ohne die Variable zu beeinflussen, von der sie ursprünglich abgeleitet wurde.

Obwohl Sie Arrays oder Funktionen nicht als Argumente übergeben können, können Sie Zeiger an diese Elemente übergeben. Zeiger bieten eine Möglichkeit, dass eine Funktion auf einen Wert über einen Verweis zugreifen kann. Da ein Zeiger auf eine Variable die Adresse der Variable enthält, kann die Funktion diese Adresse verwenden, um auf den Wert der Variable zuzugreifen. Zeigerargumente ermöglichen einer Funktion den Zugriff auf Arrays und Funktionen, obwohl Arrays und Funktionen nicht als Argumente übergeben werden können.

Die Reihenfolge, in der Argumente ausgewertet werden, kann zwischen den verschiedenen Compilern und Optimierungsebenen variieren. Allerdings werden die Argumente und alle Nebeneffekte vollständig ausgewertet, bevor die Funktion eingegeben wird. Weitere Informationen zu Nebeneffekten finden Sie unter [Nebeneffekte](../c-language/side-effects.md).

Die *expression-list* in einem Funktionsaufruf wird ausgewertet und die üblichen arithmetischen Konvertierungen werden für jedes Argument im Funktionsaufruf durchgeführt. Wenn ein Prototyp verfügbar ist, wird der resultierende Argumenttyp mit dem entsprechenden Parameter des Prototyps verglichen. Wenn sie nicht übereinstimmen, wird entweder eine Konvertierung durchgeführt oder eine Diagnosemeldung ausgegeben. Die Parameter können auch die üblichen arithmetischen Konvertierungen durchlaufen.

Die Anzahl von Ausdrücken in *expression-list* muss mit der Anzahl von Parametern übereinstimmen, es sei denn, der Prototyp oder die Definition der Funktion gibt explizit eine variable Anzahl von Argumenten an. In diesem Fall überprüft der Compiler so viele Argumente wie Typnamen in der Liste von Parametern vorhanden sind, und konvertiert sie ggf. wie oben beschrieben. Weitere Informationen finden Sie unter [Aufrufe mit einer variablen Anzahl von Argumenten](../c-language/calls-with-a-variable-number-of-arguments.md).

Wenn die Parameterliste des Prototyps nur das Schlüsselwort **`void`** enthält, erwartet der Compiler keine Argumente im Funktionsaufruf und keine Parameter in der Definition. Eine Diagnosemeldung wird ausgegeben, wenn Argumente gefunden werden.

## <a name="example"></a>Beispiel

In diesem Beispiel werden Zeiger als Argumente verwendet:

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

In diesem Beispiel wird die `swap`-Funktion in `main` deklariert, um zwei Argumente zu erhalten, die von den Bezeichnern `num1` bzw. `num2` dargestellt werden, die beide Zeiger auf **`int`** -Werte sind. Die Parameter `num1` und `num2` in der Prototypdefinition werden ebenfalls als Zeiger auf **`int`** -Typwerte deklariert.

Im Funktionsaufruf

```C
swap( &x, &y )
```

wird die Adresse von `x` in `num1` und die Adresse von `y` in `num2` gespeichert. Jetzt gibt es zwei Namen oder "Aliase" für denselben Speicherort. Verweise auf `*num1` und `*num2` in `swap` sind gewissermaßen Verweise auf `x` und `y` in `main`. Die Zuweisungen innerhalb von `swap` tauschen tatsächlich den Inhalt von `x` und `y` aus. Daher ist keine **`return`** -Anweisung erforderlich.

Der Compiler führt eine Typüberprüfung auf den Argumenten zu `swap` aus, da der Prototyp von `swap` Argumenttypen für jeden Parameter einschließt. Die Bezeichner innerhalb der Klammern des Prototyps und der Definition können gleich oder unterschiedlich sein. Wichtig ist, dass die Typen der Argumente mit denen der Parameterlisten im Prototyp und in der Definition übereinstimmen.

## <a name="see-also"></a>Siehe auch

[Funktionsaufrufe](../c-language/function-calls.md)
