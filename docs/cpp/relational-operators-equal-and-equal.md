---
title: 'Relationale Operatoren: &lt; , &gt; , &lt; = und&gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 81421a135059b8804955d472365ebef9802d3210
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227113"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Relationale Operatoren: &lt; , &gt; , &lt; = und&gt;=

## <a name="syntax"></a>Syntax

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Bemerkungen

Die binären relationalen Operatoren bestimmen die folgenden Beziehungen:

- Kleiner als ( **\<** )

- Größer als ( **>** )

- Kleiner als oder gleich ( **\<=** )

- Größer als oder gleich ( **>=** )

Die relationalen Operatoren haben Assoziativität von links nach rechts. Beide Operanden aus relationalen Operatoren müssen vom arithmetischen oder vom Zeigertyp sein. Sie liefern Werte vom Typ **`bool`** . Der zurückgegebene Wert ist **`false`** (0), wenn die Beziehung im Ausdruck false ist. andernfalls ist der zurückgegebene Wert **`true`** (1).

## <a name="example"></a>Beispiel

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

Die Ausdrücke im vorangehenden Beispiel müssen in Klammern eingeschlossen werden, da der Stream-Einfügungs Operator ( **<<** ) Vorrang vor den relationalen Operatoren hat. Daher würde der erste Ausdruck ohne Klammern wie folgt ausgewertet:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Die üblichen arithmetischen Konvertierungen, die in [Standard Konvertierungen](standard-conversions.md) abgedeckt werden, werden auf Operanden arithmetischer Typen angewendet.

## <a name="comparing-pointers"></a>Vergleichen von Zeigern

Wenn zwei Zeiger auf Objekte vom gleichen Typs verglichen werden, wird das Ergebnis nach der Position der Objekte bestimmt, auf die im Adressbereich des Programms gezeigt wird. Zeiger können auch mit einem konstanten Ausdruck verglichen werden, der als 0 (null) oder einem Zeiger vom Typ ausgewertet wird `void *` . Wenn ein Zeiger Vergleich für einen Zeiger vom Typ erfolgt `void *` , wird der andere Zeiger implizit in den Typ konvertiert `void *` . Anschließend wird verglichen.

Zwei Zeiger verschiedener Typen können nicht verglichen werden, es sei denn:

- Ein Typ ist ein Klassentyp, der vom anderen Typ abgeleitet wird.

- Mindestens einer der Zeiger wird explizit in den Typ konvertiert (cast) `void *` . (Der andere Zeiger wird implizit in den Typ `void *` für die Konvertierung konvertiert.)

Zwei Zeiger desselben Typs, die auf dasselbe Objekt zeigen, sind beim Vergleich garantiert gleich. Wenn zwei Zeiger auf nicht statische Member eines Objekts verglichen werden, gelten folgende Regeln:

- Wenn der Klassentyp kein ist **`union`** und die beiden Member nicht durch einen *Zugriffsspezifizierer*, z. b. **`public`** , oder, getrennt sind **`protected`** **`private`** , vergleicht der Zeiger auf den zuletzt deklarierten Member größer als der Zeiger auf den zuvor deklarierten Member.

- Wenn die beiden Member durch einen *Zugriffsspezifizierer*getrennt sind, sind die Ergebnisse nicht definiert.

- Wenn der Klassentyp ein ist **`union`** , werden Zeiger auf verschiedene Datenmember in, die **`union`** gleich sind.

Wenn zwei Zeiger auf Elemente desselben Arrays oder auf ein Element über das Ende des Arrays hinaus zeigen, erzielt der Zeiger auf das Objekt mit dem höheren Index einen höheren Wert. Der Vergleich von Zeigern ist nur dann garantiert gültig, wenn der Zeiger auf Objekte im gleichen Array oder auf die Position verweist, die eine Stelle nach dem Ende des Arrays liegt.

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C relationale und Gleichheits Operatoren](../c-language/c-relational-and-equality-operators.md)
