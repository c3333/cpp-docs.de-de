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
ms.openlocfilehash: 729e173c695db3b4970490e84bedfd441e6ff6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344836"
---
# <a name="usual-arithmetic-conversions"></a>Übliche arithmetische Konvertierungen

Die meisten C-Operatoren führen Typkonvertierungen aus, um die Operanden eines Ausdrucks in einen allgemeinen Typ zu bringen oder um kurze Werte auf die ganzzahlige Größe zu erweitern, die bei Computervorgängen verwendet wird. Die Konvertierungen, die von C-Operatoren ausgeführt werden, hängen vom bestimmten Operator und dem Typ des Operanden oder der Operanden ab. Viele Operatoren führen jedoch ähnliche Konvertierungen für Operanden des Ganzzahl- und Gleitkommatyps aus. Diese Konvertierungen werden als "arithmetische Konvertierungen" bezeichnet. Die Konvertierung eines Operandenwerts in einen kompatiblen Typ bewirkt keine Änderung an seinem Wert.

Die unten zusammengefassten arithmetischen Konvertierungen werden als "übliche arithmetische Konvertierungen" bezeichnet. Diese Schritte werden nur für binäre Operatoren angewendet, die einen arithmetischen Typ erwarten. Der Zweck besteht darin, einen allgemeinen Typ zu erhalten, der gleichzeitig der Ergebnistyp ist. Um zu bestimmen, welche Konvertierungen tatsächlich durchgeführt werden, wird der folgende Algorithmus vom Compiler auf binäre Operationen im Ausdruck angewendet. Die folgenden Schritte sind in beliebiger Reihenfolge aufgeführt.

1. Wenn einer der beiden Operanden vom Typ `long double` ist, wird der andere Operand in den Typ `long double` umgewandelt.

1. Wenn die oben genannte Bedingung nicht erfüllt wird und ein Operand den Typ **double** aufweist, wird der andere Operand in den Typ **double** konvertiert.

1. Wenn die oben genannten zwei Bedingungen nicht erfüllt werden und ein Operand den Typ **float** aufweist, wird der andere Operand in den Typ **float** konvertiert.

1. Wenn die oben genannten drei Bedingungen nicht erfüllt werden (keiner der Operanden ist ein Gleitkommatyp), werden die Ganzzahlkonvertierungen für den Operanden wie folgt ausgeführt:

   - Wenn einer der beiden Operanden vom Typ `unsigned long` ist, wird der andere Operand in den Typ `unsigned long` umgewandelt.

   - Wenn die vorherige Bedingung nicht erfüllt ist und einer der beiden Operanden vom Typ **long** und der andere vom Typ `unsigned int` ist, werden beide Operanden in den Typ `unsigned long` konvertiert.

   - Wenn die oben genannten beiden Bedingungen nicht erfüllt werden und ein Operand den Typ **long** aufweist, wird der andere Operand in den Typ **long** konvertiert.

   - Wenn die oben genannten drei Bedingungen nicht erfüllt werden und ein Operand den Typ `unsigned int` aufweist, wird der andere Operand in den Typ `unsigned int` umgewandelt.

   - Wenn keine der oben genannten Bedingungen erfüllt wird, werden beide Operanden in den Typ `int` umgewandelt.

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
