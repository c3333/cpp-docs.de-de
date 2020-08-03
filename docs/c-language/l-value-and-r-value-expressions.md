---
title: L-Wert- und R-Wert-Ausdrücke
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: 0c287c45f2d7ea121c9c706b3b761ff7ce6ec232
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199827"
---
# <a name="l-value-and-r-value-expressions"></a>L-Wert- und R-Wert-Ausdrücke

Ausdrücke, die auf Speicheradressen verweisen, werden als "L-Wertausdrücke" bezeichnet. Ein L-Wert stellt einen "Lokatorwert" des Speicherbereichs bzw. einen "linken" Wert dar, der besagt, dass der Wert links neben dem Gleichzeichen ( **=** ) stehen kann. Häufig sind L-Werte Bezeichner.

Ausdrücke, die auf änderbare Speicherorte verweisen, werden als "änderbare L-Werte" bezeichnet. Ein änderbarer L-Wert darf weder einen Arraytyp noch einen unvollständigen Typ oder einen Typ mit dem Attribut **`const`** aufweisen. Damit Strukturen und Unions änderbare L-Werte sein können, dürfen sie keine Member mit dem Attribut **`const`** enthalten. Der Name des Bezeichners gibt einen Speicherort an, und der Wert der Variable ist der an diesem Speicherort gespeicherte Wert.

Ein Bezeichner ist ein änderbarer L-Wert, wenn er auf einen Speicherbereich verweist und einen arithmetischen Typ oder einen Struktur-, Union- oder Zeigertyp aufweist. Wenn beispielsweise `ptr` ein Zeiger auf einen Speicherbereich ist, dann ist `*ptr` ein änderbarer L-Wert, der den Speicherbereich angibt, auf den `ptr` zeigt.

Jeder der folgenden C-Ausdrücke kann ein L-Wertausdruck sein:

- Ein Bezeichner des Ganzzahl-, Gleitkomma-, Zeiger-, Struktur- oder Union-Typs

- Ein Subscriptausdruck ( **[ ]** ), der nicht als Array ausgewertet wird

- Ein Memberauswahlausdruck ( **->** oder **.** )

- Ein unärer Dereferenzierungsausdruck (<strong>\*</strong>), der nicht auf ein Array verweist

- Ein L-Wertausdruck in Klammern

- Ein **`const`** -Objekt (ein nicht änderbarer L-Wert)

Gelegentlich wird der Begriff "R-Wert" verwendet, um den Wert eines Ausdrucks zu beschreiben und ihn von einem L-Wert zu unterscheiden. Alle L-Werte sind R-Werte, aber nicht alle R-Werte sind L-Werte.

**Microsoft-spezifisch**

Microsoft C enthält eine Erweiterung für den ANSI C-Standard, mit dem umgewandelte L-Werte als L-Werte genutzt werden können, sofern die Objektgröße durch die Umwandlung nicht verlängert wird. (Weitere Informationen finden Sie unter [Typumwandlungskonvertierungen](../c-language/type-cast-conversions.md).) Diese Funktion wird anhand des folgenden Beispiels veranschaulicht:

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Bei Microsoft C sind die Microsoft-Erweiterungen standardmäßig aktiviert. Verwenden Sie die /Za-Compileroption, um diese Erweiterungen zu deaktivieren.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Operanden und Ausdrücke](../c-language/operands-and-expressions.md)
