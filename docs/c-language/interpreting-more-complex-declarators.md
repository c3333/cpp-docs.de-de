---
title: Interpretieren von komplexeren Deklaratoren
ms.date: 11/04/2016
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
ms.openlocfilehash: 385392ea8836998e71584d02bd0ee4478fb774a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199905"
---
# <a name="interpreting-more-complex-declarators"></a>Interpretieren von komplexeren Deklaratoren

Sie können einen beliebigen Deklarator in Klammern einschließen, um eine bestimmte Interpretation eines "komplexen Deklarators" anzugeben. Ein komplexer Deklarator ist ein Bezeichner, der durch mehr als einen Array-, Zeiger- oder Funktionsmodifizierer qualifiziert wird. Sie können verschiedene Kombinationen von Array-, Zeiger- und Funktionsmodifizierern auf einen einzelnen Bezeichner anwenden. Im Allgemeinen kann **`typedef`** verwendet werden, um Deklarationen zu vereinfachen. Weitere Informationen finden Sie unter [Typedef-Deklarationen](../c-language/typedef-declarations.md).

Bei der Interpretation komplexer Deklaratoren haben runde und eckige Klammern (das heißt, Modifizierer auf der rechten Seite des Bezeichners) Vorrang vor Sternchen (das heißt, Modifizierer auf der linken Seite des Bezeichners). Eckige Klammern und runde Klammern haben den gleichen Rang und sind von von links nach rechts angeordnet. Nachdem der Deklarator vollständig interpretiert worden ist, wird der Typspezifizierer während des letzten Schritts übernommen. Indem Sie Klammern verwenden, können Sie die Standardreihenfolge der Zuordnung überschreiben und eine bestimmte Interpretation erzwingen. Verwenden Sie jedoch niemals Klammern um einen Bezeichnernamen selbst. Dies könnte fälschlicherweise als Parameterliste interpretiert werden.

Eine einfache Möglichkeit, komplexe Deklaratoren zu interpretieren, besteht darin, sie mithilfe der folgenden vier Schritte "von innen nach außen" zu lesen:

1. Beginnen Sie mit dem Bezeichner, und suchen Sie rechts nach Klammern (sofern vorhanden).

1. Interpretieren Sie diese eckigen oder runden Klammern, und suchen Sie links nach Sternchen.

1. Wenn Sie zu einem beliebigen Zeitpunkt auf eine rechte Klammer stoßen, gehen Sie zurück, und wenden Sie die Regeln 1 und 2 auf alles innerhalb der Klammer an.

1. Wenden Sie den Typspezifizierer an.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

In diesem Beispiel werden die Schritte in der entsprechenden Reihenfolge nummeriert und können wie folgt interpretiert werden:

1. Der Bezeichner `var` wird deklariert als

1. ein Zeiger auf

1. eine Funktion, die

1. ein Zeiger auf

1. ein Array mit 10 Elementen zurückgibt, die

1. Zeiger auf

1. **`char`** -Werte sind.

## <a name="examples"></a>Beispiele

Die folgenden Beispiele veranschaulichen weitere komplexe Deklarationen und zeigen, wie sich Klammern auf die Bedeutung einer Deklaration auswirken können.

```
int *var[5]; /* Array of pointers to int values */
```

Der Arraymodifizierer hat eine höhere Priorität als der Zeigermodifizierer, daher wird `var` als Array deklariert. Der Zeigermodifizierer gilt für den Typ der Arrayelemente. Also sind die Arrayelemente Zeiger auf **`int`** -Werte.

```
int (*var)[5]; /* Pointer to array of int values */
```

In dieser Deklaration für `var` geben Klammern dem Zeigermodifizierer höhere Priorität als dem Arraymodifizierer, und `var` wird als Zeiger auf ein Array von fünf **`int`** -Werten deklariert.

```
long *var( long, long ); /* Function returning pointer to long */
```

Funktionsmodifizierer verfügen ebenfalls über eine höhere Priorität als Zeigermodifizierer, weshalb `var` bei dieser Deklaration für `var` als Funktion deklariert wird, die einen Zeiger auf einen **`long`** -Wert zurückgibt. Die Funktion wird deklariert, um zwei **`long`** -Werte als Argumente abzurufen.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Dieses Beispiel ähnelt dem vorherigen. Klammern geben dem Zeigermodifizierer höhere Priorität als dem Funktionsmodifizierer, und `var` wird als Zeiger auf eine Funktion deklariert, die einen **`long`** -Wert zurückgibt. Außerdem akzeptiert die Funktion zwei **`long`** -Argumente.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Die Elemente eines Arrays können keine Funktionen sein, sondern diese Deklaration zeigt, wie Sie stattdessen einen Array von Zeigern auf Funktionen deklarieren. In diesem Beispiel wird `var` als ein Array von fünf Zeigern auf Funktionen deklariert, die Strukturen mit zwei Membern zurückgeben. Die Argumente für die Funktionen werden als zwei Strukturen vom selben Strukturtyp, `both`, deklariert. Beachten Sie, dass die Klammern, die `*var[5]` umgeben, erforderlich sind. Ohne diese stellt die Deklaration einen ungültigen Versuch dar, ein Array von Funktionen zu deklarieren, wie im Folgenden dargestellt:

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

Die folgende Anweisung deklariert einen Array von Zeigern.

```
unsigned int *(* const *name[5][10] ) ( void );
```

Das `name`-Array besteht aus 50 Elementen, die in einem mehrdimensionalen Array angeordnet sind. Die Elemente sind Zeiger auf einen Zeiger, der eine Konstante ist. Dieser konstante Zeiger zeigt auf eine Funktion, die über keine Parameter verfügt und einen Zeiger auf einen Typ ohne Vorzeichen zurückgibt.

Im folgenden Beispiel wird eine Funktion veranschaulicht, die einen Zeiger auf ein Array mit drei **`double`** -Werten zurückgibt.

```
double ( *var( double (*)[3] ) )[3];
```

In dieser Deklaration gibt eine Funktion einen Zeiger auf ein Array zurück, da Funktionen, die Arrays zurückgeben, ungültig sind. Hier wird `var` als Funktion deklariert, die einen Zeiger auf ein Array mit drei **`double`** -Werten zurückgibt. Die Funktion `var` ruft ein Argument ab. Das Argument, zum Beispiel der Rückgabewert, ist ein Zeiger auf ein Array von drei **`double`** -Werten. Der Argumenttyp wird von einem komplexen *abstract-declarator* angegeben. Das Sternchen im Argumenttyp muss in Klammern gesetzt werden. Ohne sie würde der Argumenttyp ein Array von drei Zeigern auf **`double`** -Werte sein. Ausführliche Informationen und Beispiele zu abstrakten Deklaratoren finden Sie unter [C-Deklaratoren (abstrakt)](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Wie im obigen Beispiel gezeigt, kann ein Zeiger auf einen anderen Zeiger zeigen, und ein Array kann Arrays als Elemente enthalten. In diesem Fall ist `var` ein Array mit fünf Elementen. Jedes Element ist ein fünf Elemente umfassendes Array von Zeigern auf Zeiger auf Unions mit zwei Membern.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Dieses Beispiel zeigt, wie das Platzieren von Klammern die Bedeutung der Deklaration ändert. In diesem Beispiel ist `var` ein fünf Elemente umfassendes Array von Zeigern auf fünf Elemente umfassende Arrays von Zeigern auf Unions. Beispiele zur Verwendung von **`typedef`** , um komplexe Deklarationen zu vermeiden, finden Sie unter [Typedef-Deklarationen](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Siehe auch

[Deklarationen und Typen](../c-language/declarations-and-types.md)
