---
title: Typqualifizierer
description: Hier werden die Typqualifizierer für die Sprache C beschrieben, die im Microsoft Visual C-Compiler verwendet werden.
ms.date: 11/6/2020
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: dd36aeb5d142eebbd6e4a339fe6c18925a6fd45a
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381609"
---
# <a name="type-qualifiers"></a>Typqualifizierer

Typqualifizierer verleihen einem Bezeichner eine von zwei Eigenschaften. Der Typqualifizierer **`const`** deklariert ein Objekt als nicht änderbar. Der Typqualifizierer **`volatile`** deklariert ein Element, bei dem eine Wertänderung von außerhalb des Programms, in dem es vorhanden ist, zulässig ist (z. B. durch einen gleichzeitig ausgeführten Thread).

Die Typqualifizierer **`const`** , **`restrict`** und **`volatile`** können pro Deklaration nur einmal verwendet werden. Typqualifizierer lassen sich mit beliebigen Typspezifizierern verwenden, dürfen aber in einer Deklaration mit mehreren Elementen nicht hinter dem ersten Komma stehen. Beispielsweise sind die folgenden Deklarationen zulässig:

```c
typedef volatile int VI;
const int ci;
```

Die folgenden Deklarationen sind nicht zulässig:

```c
typedef int *i, volatile *vi;
float f, const cf;
```

Typqualifizierer sind nur wichtig, wenn auf Bezeichner als L-Werte in Ausdrücken zugegriffen wird. Weitere Informationen über L-Werte und Ausdrücke finden Sie unter [L-Wert- und R-Wert-Ausdrücke](../c-language/l-value-and-r-value-expressions.md).

## <a name="syntax"></a>Syntax

*`type-qualifier`*:\
&emsp;**`const`**\
&emsp;**`restrict`**\
&emsp;**`volatile`**

## <a name="const-and-volatile"></a>`const` und `volatile`

Folgende **`const`** - und **`volatile`** -Deklarationen sind zulässig:

```c
int const *p_ci;      // Pointer to constant int
int const (*p_ci);   // Pointer to constant int
int *const cp_i;     // Constant pointer to int
int (*const cp_i);   // Constant pointer to int
int volatile vint;     // Volatile integer
```

Wenn die Spezifikation eines Arraytyps Typqualifizierer enthält, wird das Element qualifiziert, nicht der Arraytyp. Enthält die Spezifikation des Funktionstyps Qualifizierer, ist das Verhalten undefiniert. **`volatile`** und **`const`** wirken sich nicht den Wertebereich oder die arithmetischen Eigenschaften des Objekts aus.

- Das **`const`** -Schlüsselwort kann verwendet werden, um jeden grundlegenden oder aggregierten Typ, einen Zeiger auf ein Objekt beliebigen Typs oder **`typedef`** zu ändern. Wenn ein Element nur mit dem **`const`** -Typqualifizierer deklariert ist, lautet der Typ **const int**. Eine **`const`** -Variable kann initialisiert oder in einen schreibgeschützten Speicherbereich eingefügt werden. Das **`const`** -Schlüsselwort ist gut geeignet, um Zeiger auf **`const`** zu deklarieren, da die Funktion den Zeiger keinesfalls ändern darf.

- Der Compiler nimmt an, dass im Programm zu jedem Zeitpunkt der Zugriff auf eine **`volatile`** -Variable durch einen unbekannten Prozess erfolgen kann, der den Wert verwendet oder ändert. Der Code für jede Zuordnung oder für jeden Verweis einer **`volatile`** -Variable muss unabhängig von den in der Befehlszeile angegebenen Optimierungen generiert werden, auch wenn er augenscheinlich keine Auswirkung hat.

Bei alleiniger Verwendung von **`volatile`** wird **`int`** angenommen. Der Typspezifizierer **`volatile`** kann verwendet werden, um zuverlässigen Zugriff auf spezielle Speicheradressen zu ermöglichen. Verwenden Sie **`volatile`** mit Datenobjekten, bei denen der Zugriff oder eine Änderung durch Signalhandler, durch gleichzeitig ausgeführte Programme oder durch spezielle Hardware (wie im Speicher abgebildete E/A-Steuerungsregister) erfolgen kann. Sie können eine Variable für ihre Lebensdauer als **`volatile`** deklarieren oder einen einzelnen Verweis in **`volatile`** umwandeln.

- Ein Element kann sowohl **`const`** als auch **`volatile`** sein. Dann ist eine Änderung des Elements durch das eigene Programm nicht zulässig, aber eine Änderung durch einen asynchronen Prozess ist möglich.
 
## `restrict`

Der in C99 eingeführte Typqualifizierer **`restrict`** kann auf Zeigerdeklarationen angewendet werden. Er qualifiziert den Zeiger, nicht das Element, auf das dieser zeigt.

**`restrict`** ist ein Optimierungshinweis an den Compiler, dass kein weiterer Zeiger im aktuellen Bereich auf dieselbe Arbeitsspeicheradresse verweist. Das bedeutet, dass während der Lebensdauer des Zeigers nur der Zeiger oder ein davon abgeleiteter Wert (z. B. Zeiger + 1) für den Zugriff auf das Objekt verwendet wird. Auf diese Weise kann der Compiler einen besser optimierten Code erzeugen. C++ weist einen ähnlichen Mechanismus auf: [`__restrict`](../cpp/extension-restrict.md).

Denken Sie daran, dass **`restrict`** ein Vertrag zwischen Ihnen und dem Compiler ist. Wenn Sie für einen mit **`restrict`** gekennzeichneten Zeiger einen Alias verwenden, ist das Ergebnis nicht definiert.

Im Folgenden sehen Sie ein Beispiel, das **`restrict`** verwendet:

```c
void test(int* restrict first, int* restrict second, int* val)
{
    *first += *val;
    *second += *val;
}

int main()
{
    int i = 1, j = 2, k = 3;
    test(&i, &j, &k);

    return 0;
}

// Marking union members restrict tells the compiler that
// only z.x or z.y will be accessed in any scope, which allows
// the compiler to optimize access to the members.
union z 
{
    int* restrict x;
    double* restrict y;
};
```

## <a name="see-also"></a>Siehe auch

[`/std` (Standardversion für die Sprache festlegen)](../build/reference/std-specify-language-standard-version.md)\
[Deklarationen und Typen](../c-language/declarations-and-types.md)
