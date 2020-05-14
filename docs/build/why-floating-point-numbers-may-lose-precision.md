---
title: Warum Gleitkommazahlen an Genauigkeit verlieren können
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298713"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Warum Gleitkommazahlen an Genauigkeit verlieren können

Für Gleitkomma-Dezimalwerte gibt es in der Regel keine genaue binäre Darstellung. Dies ist eine Nebenwirkung davon, wie die CPU Gleitkommadaten darstellt. Aus diesem Grund kann es zu einem gewissen Genauigkeitsverlust kommen, und einige Gleitkommavorgänge können zu unerwarteten Ergebnissen führen.

Dieses Verhalten hat eine der folgende Ursachen:

- Die binäre Darstellung der Dezimalzahl ist möglicherweise nicht genau.

- Es gibt einen Typenkonflikt zwischen den verwendeten Zahlen (z. B. gleichzeitige Verwendung von „float“ und „double“).

Um dieses Verhalten zu korrigieren, stellen die meisten Programmierer entweder sicher, dass der Wert größer oder kleiner als erforderlich ist, oder sie verwenden eine zu diesem Zweck beschaffte Bibliothek für binär codierte Dezimalzahlen (BCD-Bibliothek), mit der die Genauigkeit gewahrt bleibt.

Die binäre Darstellung von Gleitkommawerten wirkt sich auf die Präzision und Genauigkeit von Gleitkommaberechnungen aus. Microsoft Visual C++ verwendet das [IEEE-Gleitkommaformat](ieee-floating-point-representation.md).

## <a name="example"></a>Beispiel

```c
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>Kommentare

Für EPSILON können Sie die Konstante FLT_EPSILON, die für „float“ als 1.192092896e-07F definiert ist, oder die Konstante DBL_EPSILON, die für „double“ als 2.2204460492503131e-016 definiert ist, verwenden. Sie müssen für diese Konstanten „float.h“ einschließen. Diese Konstanten werden als kleinste positive Zahl x definiert, sodass x+1.0 nicht gleich 1.0 ist. Da es sich um eine sehr kleine Zahl handelt, sollten Sie eine benutzerdefinierte Toleranz für Berechnungen verwenden, die sehr große Zahlen umfassen.

## <a name="see-also"></a>Siehe auch

[Codeoptimierung](optimizing-your-code.md)
