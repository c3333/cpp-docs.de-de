---
title: Übliche arithmetische Konvertierungen
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
ms.openlocfilehash: 7e28c8a234ff840a16228416720ac48763fccc76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231415"
---
# <a name="usual-arithmetic-conversions"></a>Übliche arithmetische Konvertierungen

Die meisten C-Operatoren führen Typkonvertierungen aus, um die Operanden eines Ausdrucks in einen allgemeinen Typ zu bringen oder um kurze Werte auf die ganzzahlige Größe zu erweitern, die bei Computervorgängen verwendet wird. Die Konvertierungen, die von C-Operatoren ausgeführt werden, hängen vom bestimmten Operator und dem Typ des Operanden oder der Operanden ab. Viele Operatoren führen jedoch ähnliche Konvertierungen für Operanden des Ganzzahl- und Gleitkommatyps aus. Diese Konvertierungen werden als "arithmetische Konvertierungen" bezeichnet. Die Konvertierung eines Operandenwerts in einen kompatiblen Typ bewirkt keine Änderung an seinem Wert.

Die unten zusammengefassten arithmetischen Konvertierungen werden als "übliche arithmetische Konvertierungen" bezeichnet. Diese Schritte werden nur für binäre Operatoren angewendet, die einen arithmetischen Typ erwarten. Der Zweck besteht darin, einen allgemeinen Typ zu erhalten, der gleichzeitig der Ergebnistyp ist. Um zu bestimmen, welche Konvertierungen tatsächlich durchgeführt werden, wird der folgende Algorithmus vom Compiler auf binäre Operationen im Ausdruck angewendet. Die folgenden Schritte sind in beliebiger Reihenfolge aufgeführt.

1. Wenn einer der beiden Operanden vom Typ **`long double`** ist, wird der andere Operand in den Typ **`long double`** konvertiert.

1. Wenn die oben genannte Bedingung nicht erfüllt wird und einer der Operanden den Typ **`double`** aufweist, wird der andere Operand in den Typ **`double`** konvertiert.

1. Wenn die beiden oben genannten Bedingungen nicht erfüllt werden und einer der Operanden den Typ **`float`** aufweist, wird der andere Operand in den Typ **`float`** konvertiert.

1. Wenn die oben genannten drei Bedingungen nicht erfüllt werden (keiner der Operanden ist ein Gleitkommatyp), werden die Ganzzahlkonvertierungen für den Operanden wie folgt ausgeführt:

   - Wenn einer der beiden Operanden vom Typ **`unsigned long`** ist, wird der andere Operand in den Typ **`unsigned long`** konvertiert.

   - Wenn die oben genannte Bedingung nicht erfüllt wird und einer der Operanden den Typ **`long`** und der andere den Typ **`unsigned int`** aufweist, werden beide Operanden in den Typ **`unsigned long`** konvertiert.

   - Wenn die beiden oben genannten Bedingungen nicht erfüllt werden und einer der Operanden den Typ **`long`** aufweist, wird der andere Operand in den Typ **`long`** konvertiert.

   - Wenn die drei oben genannten Bedingungen nicht erfüllt werden und einer der Operanden den Typ **`unsigned int`** aufweist, wird der andere Operand in den Typ **`unsigned int`** konvertiert.

   - Wenn keine der oben genannten Bedingungen erfüllt wird, werden beide Operanden in den Typ **`int`** konvertiert.

Das folgende Codebeispiel veranschaulicht diese Konvertierungsregeln:

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>Siehe auch

[C-Operatoren](../c-language/c-operators.md)
