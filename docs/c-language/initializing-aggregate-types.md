---
title: Initialisierung von Aggregattypen
ms.date: 11/04/2016
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
ms.openlocfilehash: b4b0dd82263781966760b6e21ef24ded56b06a01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229622"
---
# <a name="initializing-aggregate-types"></a>Initialisierung von Aggregattypen

Ein *aggregierter* Typ ist eine Struktur, eine Union oder ein Arraytyp. Wenn ein aggregierter Typ Member von aggregierten Typen enthält, werden die Initialisierungsregeln rekursiv angewendet.

## <a name="syntax"></a>Syntax

*initializer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{**  *Initialisiererliste*  **}** /* Für Aggregatinitialisierung \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{**  *Initialisiererliste*  **, }**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Initialisiererliste*  **,**  *Initialisierer*

Die *initializer-list* ist eine Liste von durch Trennzeichen getrennten Initialisierungen. Jeder Initialisierer in der Liste ist entweder ein konstanter Ausdruck oder eine Initialisiererliste. Daher können Initialisierungslisten geschachtelt sein. Diese Form dient zur Initialisierung aggregierter Member eines aggregierten Typs, wie in den Beispielen in diesem Abschnitt gezeigt. Wenn der Initialisierer für einen automatischen Bezeichner jedoch ein einzelner Ausdruck ist, muss er kein konstanter Ausdruck sein. Er muss lediglich einen geeigneten Typ für die Zuweisung zum Bezeichner aufweisen.

Für jede Initialisiererliste werden den entsprechenden Membern der aggregierten Variable die Werte der konstanten Ausdrücke in der jeweiligen Reihenfolge zugewiesen.

Wenn *initializer-list* über weniger Werte als ein aggregierter Typ verfügt, werden die verbleibenden Member oder Elemente des aggregierten Typs auf 0 (null) initialisiert. Der Anfangswert eines automatischen Bezeichners, der nicht explizit initialisiert wird, ist nicht definiert. Wenn *initializer-list* mehr Werte als ein aggregierter Typ aufweist, wird ein Fehler ausgegeben. Diese Regeln gelten für jede eingebettete Initialisiererliste sowie für das Aggregat als Ganzes.

Der Initialisierer einer Struktur ist entweder ein Ausdruck vom gleichen Typ oder eine Liste mit Initialisierern für seine Member, die in geschweifte Klammern ( **{ }** ) stehen. Unbenannte Bitfeldmember werden nicht initialisiert.

Wenn eine Union initialisiert wird, muss *initializer-list* ein einzelner konstanter Ausdruck sein. Der Wert des konstanten Ausdrucks wird dem ersten Member der Union zugewiesen.

Wenn ein Array eine unbekannte Größe hat, bestimmt die Anzahl der Initialisierer die Größe des Arrays, und sein Typ wird vollständig. Es gibt keine Möglichkeit, die Wiederholung eines Initialisierers in C anzugeben bzw. ein Element in der Mitte eines Arrays zu initialisieren, ohne alle vorangehenden Werte ebenfalls bereitzustellen. Wenn Sie diesen Vorgang im Programm benötigen, schreiben Sie die Routine in der Assemblysprache.

Beachten Sie, dass die Anzahl von Initialisierern die Arraygröße festlegen kann:

```C
int x[ ] = { 0, 1, 2 }
```

Wenn Sie die Größe festlegen und die falsche Anzahl von Initialisierern angeben, generiert der Compiler jedoch einen Fehler.

**Microsoft-spezifisch**

Die maximale Größe für ein Array wird durch **size_t** definiert. **size_t** ist in der Headerdatei STDDEF.H definiert und ein **`unsigned int`** mit dem Bereich 0x00000000 bis 0x7CFFFFFF.

**Ende Microsoft-spezifisch**

## <a name="examples"></a>Beispiele

Dieses Beispiel zeigt Initialisierer für ein Array an.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Diese Anweisung deklariert `P` als 4-mal-3-Array und initialisiert die Elemente der ersten Zeile auf 1, die Elemente der zweiten Zeile auf 2 usw. bis zur vierten Zeile. Beachten Sie, dass die Initialisiererliste für die dritte und vierte Zeile nach dem letzten konstanten Ausdruck Kommas enthält. Der letzten Initialisiererliste (`{4, 4, 4,},`) folgt ebenfalls ein Komma. Diese zusätzlichen Kommas sind zulässig, jedoch nicht erforderlich. Nur die Kommas, die konstante Ausdrücke voneinander trennen und diejenigen, die separate Initialisiererlisten voneinander trennen, sind erforderlich.

Wenn ein aggregierter Member keine eingebettete Initialisiererliste aufweist, werden einfach jedem Member des Unteraggregats Werte in der jeweiligen Reihenfolge zugewiesen. Daher entspricht die Initialisierung im vorherigen Beispiel Folgendem:

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Geschweifte Klammern können auch um einzelne Initialisierer in der Liste stehen und würden helfen, das obenstehende Beispiel zu verdeutlichen.

Wenn Sie eine aggregierte Variable initialisieren, müssen Sie darauf achten, geschweifte Klammern und Initialisiererlisten ordnungsgemäß zu verwenden. Das folgende Beispiel veranschaulicht ausführlicher, wie der Compiler geschweifte Klammern interpretiert:

```C
typedef struct
{
    int n1, n2, n3;
} triplet;

triplet nlist[2][3] =
{
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */
};
```

In diesem Beispiel wird `nlist` als ein 2-mal-3-Array von Strukturen deklariert, wobei jede Struktur über drei Member verfügt. Zeile 1 der Initialisierung weist Werte zur ersten Zeile von `nlist` zu, und zwar wie folgt:

1. Die erste linke geschweifte Klammer in Zeile 1 signalisiert dem Compiler, dass die Initialisierung des ersten aggregierten Members von `nlist` (also `nlist[0]`) beginnt.

1. Die zweite linke geschweifte Klammer gibt an, dass die Initialisierung des ersten aggregierten Members von `nlist[0]` (also die Struktur unter `nlist[0][0]`) beginnt.

1. Die erste rechte geschweifte Klammer beendet die Initialisierung der Struktur `nlist[0][0]`. Die folgende linke geschweifte Klammer leitet die Initialisierung von `nlist[0][1]` ein.

1. Der Prozess wird bis zum Ende der Zeile fortgesetzt, in der die schließende rechte geschweifte Klammer die Initialisierung von `nlist[0]` beendet.

Zeile 2 weist auf ähnliche Weise Werte zur zweiten Zeile von `nlist` zu. Beachten Sie, dass die äußeren Gruppen von geschweiften Klammern, welche die Initialisierer in den Zeilen 1 und 2 enthalten, erforderlich sind. Die folgende Konstruktion, in der die äußeren Klammern weggelassen sind, würde einen Fehler verursachen:

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

In dieser Konstruktion beginnt die erste linke geschweifte Klammer in Zeile 1 die Initialisierung von `nlist[0]`, einem Array mit drei Strukturen. Die Werte 1, 2 und 3 werden den drei Membern der ersten Struktur zugewiesen. Wenn die folgende rechte geschweifte Klammer gefunden wird (nach dem Wert 3), ist die Initialisierung von `nlist[0]` abgeschlossen und die beiden verbleibenden Strukturen im Dreistrukturarray werden automatisch auf 0 initialisiert. Entsprechend initialisiert `{ 4,5,6 }` die erste Struktur in der zweiten Zeile von `nlist`. Die verbleibenden beiden Strukturen von `nlist[1]` werden auf 0 festgelegt. Wenn der Compiler auf die folgende Initialisiererliste (`{ 7,8,9 }`) trifft, wird versucht, `nlist[2]` zu initialisieren. Da `nlist` nur über zwei Zeilen verfügt, verursacht dieser Versuch einen Fehler.

Im nächsten Beispiel werden die drei **`int`** -Member von `x` mit 1, 2 bzw. 3 initialisiert.

```C
struct list
{
    int i, j, k;
    float m[2][3];
} x = {
        1,
        2,
        3,
       {4.0, 4.0, 4.0}
      };
```

In der Struktur `list` oben werden die drei Elemente in der ersten Zeile von `m` auf 4,0 initialisiert. Die Elemente der verbleibenden Zeile von `m` werden standardmäßig auf 0,0 initialisiert.

```C
union
{
    char x[2][3];
    int i, j, k;
} y = { {
            {'1'},
            {'4'}
        }
      };
```

Die Unionvariable, in diesem Beispiel `y`, wird initialisiert. Das erste Element der Union ist ein Array, sodass der Initialisierer ein aggregierter Initialisierer ist. Die Initialisiererliste `{'1'}` weist der ersten Zeile des Arrays Werte zu. Da nur ein Wert in der Liste angezeigt wird, wird das Element in der ersten Spalte auf das Zeichen `1` initialisiert, und die übrigen zwei Elemente in der Zeile werden standardmäßig auf den Wert 0 initialisiert. Entsprechend wird das erste Element der zweiten Zeile von `x` auf das Zeichen `4` initialisiert, und die übrigen zwei Elemente in der Zeile werden auf den Wert 0 initialisiert.

## <a name="see-also"></a>Siehe auch

[Initialisierung](../c-language/initialization.md)
