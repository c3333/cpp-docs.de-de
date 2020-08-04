---
title: Mehrdimensionale Arrays (C)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
ms.openlocfilehash: f94cdff03763f689edbdedffad4ac56abec5ee53
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218831"
---
# <a name="multidimensional-arrays-c"></a>Mehrdimensionale Arrays (C)

Ein indexierte Ausdruck kann auch mehrere Indizes haben, wie folgt:

```
expression1 [ expression2 ] [ expression3 ] ...
```

indexierte Ausdrücke sind von links nach rechts angeordnet. Der äußerste linke Indexausdruck *Ausdruck1* **[** *Ausdruck2* **]** wird zuerst ausgewertet. Die Adresse, die sich aus dem Hinzufügen von *expression1* und *expression2* ergibt, bildet einen Zeigerausdruck. Dann wird *expression3* zu diesem Zeigerausdruck hinzugefügt, um einen neuen Zeigerausdruck zu bilden. Dies geht so lange weiter, bis der letzte Subscriptausdruck hinzugefügt wurde. Der Dereferenzierungsoperator (<strong>\*</strong>) wird angewendet, nachdem der letzte indexierte Ausdruck ausgewertet ist, es sei denn, der finale Zeigerwert spricht einen Arraytypen an (siehe Beispiele unten).

Ausdrücke mit mehreren Indizes verweisen auf Elemente aus "mehrdimensionalen Arrays". Ein mehrdimensionales Array ist ein Array, dessen Elemente Arrays sind. Beispielsweise ist das erste Element eines dreidimensionalen Arrays ein Array mit zwei Dimensionen.

## <a name="examples"></a>Beispiele

In den folgenden Beispielen wird ein Array mit dem Namen `prop` mit drei Elementen deklariert, von denen jedes ein 4-mal-6-Array von **`int`** -Werten ist.

```
int prop[3][4][6];
int i, *ip, (*ipp)[6];
```

Ein Verweis auf das `prop`-Array sieht wie folgt aus:

```
i = prop[0][0][1];
```

Das obige Beispiel zeigt, wie auf das zweite einzelne **`int`** -Element von `prop` verwiesen wird. Arrays werden zeilenweise gespeichert. Daher unterscheidet sich der letzte Index am schnellsten; der Ausdruck `prop[0][0][2]` verweist auf das nächste (dritte) Element des Arrays usw.

```
i = prop[2][1][3];
```

Diese Anweisung ist ein komplexerer Verweis auf ein einzelnes Element von `prop`. Der Ausdruck wird wie folgt ausgewertet:

1. Der erste Index, `2`, wird mit der Größe eines 4-mal-6- **`int`** -Arrays multipliziert und zum Zeigerwert `prop` addiert. Das Ergebnis zeigt auf das dritte 4-mal-6-Array von `prop`.

1. Der zweite Index, `1`, wird mit der Größe des **`int`** -Arrays mit 6 Elementen multipliziert und zur Adresse addiert, die von `prop[2]` dargestellt wird.

1. Jedes Element des Arrays mit 6 Elementen ist ein **`int`** -Wert, sodass der endgültige Index, `3`, mit der Größe eines **`int`** multipliziert wird, bevor er zu `prop[2][1]` hinzugefügt wird. Der resultierende Zeiger gibt das vierte Element des Arrays mit 6 Elementen an.

1. Der Dereferenzierungsoperator wird auf den Zeigerwert angewendet. Das Ergebnis ist das **`int`** -Element an dieser Adresse.

Die beiden folgenden Beispielen zeigen Fälle, in denen der Dereferenzierungsoperator nicht angewendet wurde.

```
ip = prop[2][1];

ipp = prop[2];
```

In der ersten dieser Anweisungen ist der Ausdruck `prop[2][1]` ein gültiger Verweis auf das dreidimensionale Array `prop`. Er verweist auf ein Array mit 6 Elementen (oben deklariert). Da der Zeigerwert ein Array adressiert, wird der Dereferenzierungsoperator nicht angewendet.

Ebenso ist das Ergebnis des Ausdrucks `prop[2]` in der zweiten Anweisung `ipp = prop[2];` ein Zeigerwert für ein zweidimensionales Array.

## <a name="see-also"></a>Siehe auch

[Subscript-Operator: ](../cpp/subscript-operator.md)
