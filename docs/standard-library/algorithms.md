---
title: Algorithmen
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: 6532cb56bb70c82525a13ba53efdd6203ebafb12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205222"
---
# <a name="algorithms"></a>Algorithmen

Algorithmen sind grundlegender Bestandteil der C++-Standardbibliothek. Algorithmen arbeiten nicht mit Containern selbst, sondern mit Iteratoren. Daher kann der gleiche Algorithmus von den meisten, wenn nicht gar allen, C++-Standardbibliothekcontainern verwendet werden. Dieser Abschnitt beschreibt die Konventionen und die Terminologie von C++-Standardbibliothekalgorithmen.

## <a name="remarks"></a>Bemerkungen

Die Beschreibungen der Algorithmusvorlagenfunktionen verwenden einige Kurznotationsausdrücke:

- Der Ausdruck "im Bereich \[ *A*, *b*)" bezieht sich auf die Sequenz von 0 (null) oder mehr diskreten Werten, beginnend mit *a* bis einschließlich *b*. Ein Bereich ist nur gültig, wenn *B* von *einem* erreichbar ist. Sie können *ein* -Objekt in einem Objekt *n* (*n*  =  *A*) speichern, das Objekt NULL oder mehrmals erhöhen (+ +*N*) und das Objekt nach einer endlichen Anzahl von Inkrementen (*n*B) gleich *B* vergleichen  ==  *B*.

- Der Ausdruck "jedes *N* im Bereich \[ *a*, *B*)" bedeutet, dass *N* mit dem Wert *A* beginnt und NULL oder mehrmals erhöht wird, bis es gleich dem Wert *B*ist. Der Fall *N*  ==  *B* liegt nicht im Bereich.

- Der Ausdruck "der niedrigste Wert von *N* im Bereich \[ *a*, *b*) für *X*" bedeutet, dass die Bedingung *x* für jedes *N* im Bereich \[ *a*, *b*) bestimmt wird, bis die Bedingung *x* erfüllt ist.

- Der Ausdruck "der höchste Wert von *N* im Bereich \[ *a*, *b*), d. h. *x* bedeutet, dass *x* für jedes *N* im Bereich \[ *a*, *b*) bestimmt wird. Die Funktion speichert immer *dann eine Kopie* von *N* , wenn die Bedingung *X* erfüllt ist. Wenn ein solcher Speicher auftritt, ersetzt die Funktion den endgültigen Wert von *N*, der *B*entspricht, mit dem Wert *K*. Bei einem bidirektionalen Iterator oder einem Iterator mit Wahl freiem Zugriff kann dies jedoch auch bedeuten, dass *N* mit dem höchsten Wert im Bereich beginnt und über den Bereich dekrementiert wird, bis die Bedingung *X* erfüllt ist.

- Ausdrücke wie z. b. *x*  -  *Y*, wobei *X* und *Y* andere Iteratoren als zufällige zugriffsiteratoren sein können, sind im mathematischen Sinn vorgesehen. Die Funktion wertet den Operator nicht notwendigerweise aus, **-** Wenn Sie einen solchen Wert bestimmen muss. Dasselbe gilt auch für Ausdrücke wie *x*  +  *n* und *x*  -  *n*, wobei *N* ein ganzzahliger Typ ist.

Mehrere Algorithmen verwenden ein Prädikat, das einen paar weisen Vergleich durchführt, z `operator==` . b. mit, um ein **`bool`** Ergebnis zu erzielen. Die Prädikatfunktion `operator==`, oder jeder Ersatz hierfür, darf keinen der beiden Operanden ändern. Es muss **`bool`** jedes Mal, wenn es ausgewertet wird, dasselbe Ergebnis erzielen, und es muss dasselbe Ergebnis erzielen, wenn eine Kopie eines der beiden Operanden für den Operanden ersetzt wird.

Mehrere Algorithmen verwenden ein Prädikat, das eine strikte schwache Sortierung für Elementpaare aus einer Sequenz anwendet. Für Prädikat *präd*(*X*, *Y*):

- Strict bedeutet, dass *pred*(*x*, *x*) "false" ist.

- Schwach bedeutet, dass *x* und *y* eine äquivalente Reihenfolge aufweisen, wenn \! *pred*(*x*, *y*)  && \! *pred*(*y*, *x*) (*x*  ==  *Y* muss nicht definiert sein).

- Die Reihenfolge bedeutet, dass *pred*(*x*, *Y*)  && *pred*(*y*, *z*) *pred*(*x*, *z*) impliziert.

Einige dieser Algorithmen verwenden implizit das Prädikat *X* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *Y*, `less` (*x*, *y*) und `greater` (*X*, *y*). Beachten Sie jedoch, dass Prädikate wie *X* \<= *Y* and *X* > =  *Y* diese Anforderung nicht erfüllen.

Eine Sequenz von Elementen, die durch Iteratoren im Bereich \[ *First*, *Last*) festgelegt ist, ist eine von Operator geordnete Sequenz **<** , wenn für jedes *N* im Bereich \[ 0, *zuletzt*  -  *zuerst*) und für jedes *M* im Bereich (*N*, *Letztes*  -  *erstes*) das Prädikat \! ( \* (*First*  +  *M*) < \* (*First*  +  *N*) "true" ist. (Beachten Sie, dass die Elemente in aufsteigender Reihenfolge sortiert werden.) Die Prädikat Funktion `operator<` oder ein beliebiger Ersatz dafür darf keinen der beiden Operanden ändern. Es muss **`bool`** jedes Mal, wenn es ausgewertet wird, dasselbe Ergebnis erzielen, und es muss dasselbe Ergebnis erzielen, wenn eine Kopie eines der beiden Operanden für den Operanden ersetzt wird. Darüber hinaus muss sie eine strikte schwache Sortierung für die verglichenen Operanden anwenden.

Eine Sequenz von Elementen, die durch Iteratoren im Bereich \[ `First` , `Last` ) festgelegt ist, ist ein Heap `operator<` , nach dem die Angabe erfolgt, wenn für jedes *N* im Bereich \[ 1, *zuletzt*  -  *zuerst*das Prädikat \! ( \* _First_  <  \* (*First*  +  *N*)) den Wert true hat. (Das erste Element ist das größte.) Die interne Struktur ist andernfalls nur den Vorlagen Funktionen [Make_heap](algorithm-functions.md#make_heap), [pop_heap](algorithm-functions.md#pop_heap)und [Push_heap](algorithm-functions.md#push_heap)bekannt. Wie bei einer geordneten Sequenz darf die Prädikat Funktion `operator<` oder ein beliebiger Ersatz dafür keinen der Operanden ändern, und Sie muss eine strikte schwache Reihenfolge für die Operanden erzwingen, die Sie vergleicht. Es muss **`bool`** jedes Mal, wenn es ausgewertet wird, dasselbe Ergebnis erzielen, und es muss dasselbe Ergebnis erzielen, wenn eine Kopie eines der beiden Operanden für den Operanden ersetzt wird.

Die Algorithmen der C++-Standard Bibliothek befinden sich in den [\<algorithm>](algorithm.md) [\<numeric>](numeric.md) Header Dateien und.

## <a name="see-also"></a>Weitere Informationen

[C++-Standard Bibliotheks Referenz](cpp-standard-library-reference.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](thread-safety-in-the-cpp-standard-library.md)
