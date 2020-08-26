---
title: '&lt;Iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 08e2051db70ee1891c7b60860c7ea0b423855be5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841921"
---
# <a name="ltiteratorgt"></a>&lt;Iterator&gt;

Definiert die primitiven Elemente von Iteratoren, vordefinierte Iteratoren sowie Stream-Iteratoren sowie einige unterstützende Vorlagen. Die vordefinierten Iteratoren beinhalten Insert- und Reverse-Adapter. Es gibt drei Klassen von Insert-Adaptern für Iteratoren: Front, Back und General. Sie bieten Einfügesemantik anstelle der Semantik zum Überschreiben, die von Iteratoren der Memberfunktion des Containers bereitgestellt wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<iterator>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

Iteratoren sind eine Verallgemeinerung von Zeigern. Die Anforderungen werden so abstrahiert, dass ein C++-Programm mit unterschiedlichen Datenstrukturen einheitlich arbeiten kann. Iteratoren dienen als Vermittler zwischen Containern und allgemeinen Algorithmen. Algorithmen sind nicht für bestimmte Datentypen definiert, sondern für Bereiche, die durch den Iterator-Typ festgelegt sind. Der Algorithmus funktioniert dann für jede Datenstruktur, die den Anforderungen des Iterators entspricht. Es wird zwischen fünf Typen oder Kategorien von Iteratoren mit jeweils eigenen Anforderungen und Funktionen unterschieden:

- Output: Kann vorwärts bewegt werden, Werte speichern, aber nicht abrufen, und wird von ostream und inserter bereitgestellt.

- Input: Kann vorwärts bewegt werden, Werte abrufen, aber nicht speichern, und wird von istream bereitgestellt.

- Forward: Kann vorwärts bewegt werden und Werte speichern sowie abrufen.

- Bidirektional: Kann vorwärts und rückwärts bewegt werden, Werte speichern und abrufen, und wird durch List, Set, Multiset, Map und Multimap bereitgestellt.

- Random-Access: Auf Elemente wird in beliebiger Reihenfolge zugegriffen, Werte können gespeichert und abgerufen werden, wird durch Vector, Deque, String und Array bereitgestellt.

Iteratoren mit höheren Anforderungen und besserem Zugriff auf Elemente können anstelle von Iteratoren mit geringeren Anforderungen verwendet werden. Wird beispielsweise ein Forward-Iterator aufgerufen, kann stattdessen auch ein Random-Access-Iterator verwendet werden.

Visual Studio besitzt zusätzliche Erweiterungen für C++-Standardbibliotheksiteratoren, um eine Vielzahl von Debugmodussituationen für aktivierte und nicht aktivierte Iteratoren zu unterstützen. Weitere Informationen finden Sie unter [Sichere Bibliotheken: C++-Standardbibliothek](../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="members"></a>Member

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[Vorwarnung](../standard-library/iterator-functions.md#advance)|Damit kann ein Iterator um eine bestimmte Anzahl von Positionen vorwärts verschoben werden.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Damit wird ein Iterator erstellt, mit dem Elemente an das Ende eines bestimmten Containers eingefügt werden können.|
|[beginnen](../standard-library/iterator-functions.md#begin)|Ruft einen Iterator für das erste Element in einem angegebenen Container ab.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Ruft einen konstanten Iterator für das erste Element in einem angegebenen Container ab.|
|[cend](../standard-library/iterator-functions.md#cend)|Ruft einen konstanten Iterator für das Element ab, das auf das letzte Element im angegebenen Container folgt.|
|[crbegin](../standard-library/iterator-functions.md#crbegin)||
|[crend](../standard-library/iterator-functions.md#crend)||
|[data](../standard-library/iterator-functions.md#data)||
|[distance](../standard-library/iterator-functions.md#distance)|Bestimmt die Anzahl von Inkrementen zwischen den durch zwei Iteratoren festgelegten Positionen.|
|[end](../standard-library/iterator-functions.md#end)|Ruft einen Iterator für das Element ab, das auf das letzte Element im angegebenen Container folgt.|
|[empty](../standard-library/iterator-functions.md#empty)||
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Damit wird ein Iterator erstellt, mit dem Elemente an den Anfang eines bestimmten Containers eingefügt werden können.|
|[Codeausschnitteinfüger](../standard-library/iterator-functions.md#inserter)|Ein Iterator-Adapter, mit dem einem Container an einem bestimmten Punkt ein neues Element hinzugefügt wird.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Erstellt ein [checked_array_iterator](../standard-library/checked-array-iterator-class.md)-Objekt, das von anderen Algorithmen verwendet werden kann. **Hinweis:** Bei dieser Funktion handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Gibt einen Move-Iterator zurück, der den bereitgestellten Iterator als gespeicherten Basis-Iterator enthält.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Erstellt ein [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)-Objekt, das von anderen Algorithmen verwendet werden kann. **Hinweis:** Bei dieser Funktion handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.|
|[Weiter](../standard-library/iterator-functions.md#next)|Führt eine bestimmte Anzahl von Iterationen aus und gibt die neue Position des Iterators zurück.|
|[prev](../standard-library/iterator-functions.md#prev)|Führt eine bestimmte Anzahl von Iterationen rückwärts aus und gibt die neue Position des Iterators zurück.|
|[rbegin](../standard-library/iterator-functions.md#rbegin)||
|[rend](../standard-library/iterator-functions.md#rend)||
|[size](../standard-library/iterator-functions.md#size)||

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator! =](../standard-library/iterator-operators.md#op_neq)|Testet, ob das Iterator-Objekt links vom Operator ungleich dem Iterator-Objekt rechts vom Operator ist.|
|[Operator = =](../standard-library/iterator-operators.md#op_eq_eq)|Testet, ob das Iterator-Objekt links vom Operator gleich dem Iterator-Objekt rechts vom Operator ist.|
|[Operator<](../standard-library/iterator-operators.md#op_lt)|Testet, ob das Iterator-Objekt links vom Operator kleiner ist als das Iterator-Objekt rechts vom Operator.|
|[KOM\<=](../standard-library/iterator-operators.md#op_gt_eq)|Testet, ob das Iterator-Objekt links vom Operator kleiner als oder gleich dem Iterator-Objekt rechts vom Operator ist.|
|[Operator>](../standard-library/iterator-operators.md#op_gt)|Testet, ob das Iterator-Objekt links vom Operator größer als das Iterator-Objekt rechts vom Operator ist.|
|[Operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Testet, ob das Iterator-Objekt links vom Operator größer als oder gleich dem Iterator-Objekt rechts vom Operator ist.|
|[Operator +](../standard-library/iterator-operators.md#op_add)|Fügt einen Offset zu einem Iterator hinzu und gibt den neuen `reverse_iterator` zurück, der auf das eingefügte Element an der neuen Offsetposition zeigt.|
|[KOM](../standard-library/iterator-operators.md#operator-)|Subtrahiert einen Iterator von einem anderen und gibt die Differenz zurück.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Die Klassen Vorlage beschreibt ein ausgabeiteratorobjekt. Elemente werden in einen Container des Typs eingefügt `Container` , auf den über das geschützte Objekt zugegriffen wird, das `pointer` als Container bezeichnet wird.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Eine Klasse, die einen Rückgabetyp für eine Funktion bereitstellt `iterator_category` , die einen bidirektionalen Iterator darstellt.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Eine Klasse, die auf ein Array mit einem Iterator vom Typ "Random-Access, Checked" zugreift. **Hinweis:** Bei dieser Klasse handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Eine Klasse, die einen Rückgabetyp für eine Funktion bereitstellt `iterator_category` , die einen forward-Iterator darstellt.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Die Klassen Vorlage beschreibt ein ausgabeiteratorobjekt. Elemente werden in einen Container des Typs eingefügt `Container` , auf den über das geschützte Objekt zugegriffen wird, das `pointer` als Container bezeichnet wird.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Eine Klasse, die einen Rückgabetyp für eine Funktion bereitstellt `iterator_category` , die einen eingabeiterator darstellt.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Die Klassen Vorlage beschreibt ein ausgabeiteratorobjekt. Elemente werden in einen Container des Typs eingefügt `Container` , auf den über das geschützte Objekt zugegriffen wird, das `pointer` als Container bezeichnet wird. Außerdem wird das geschützte `iterator` Objekt der Klasse mit dem `Container::iterator` Namen gespeichert `iter` .|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Die Klassen Vorlage beschreibt ein eingabeiteratorobjekt. Sie extrahiert Objekte der Klasse `Ty` aus einem Eingabestream, auf den Sie über ein Objekt zugreift, das vom Typ Zeiger auf gespeichert wird `basic_istream` \<**Elem**, **Tr**> .|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Die Klassen Vorlage beschreibt ein eingabeiteratorobjekt. Die Elemente der Klasse `Elem` werden in einen ausgabestreampuffer eingefügt, auf den Sie über ein Objekt, das Sie speichert, vom Typ `pointer` auf zugreifen `basic_streambuf` \<**Elem**, **Tr**> .|
|[Iterator](../standard-library/iterator-struct.md)|Die Klassen Vorlage wird als Basistyp für alle Iteratoren verwendet.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Eine Hilfsklasse für Vorlagen, die wichtige Typen bereitstellt, die mit verschiedenen Iterator-Typen verknüpft sind, damit die Verweise auf dieselbe Weise funktionieren.|
|[move_iterator](../standard-library/move-iterator-class.md)|Ein `move_iterator`-Objekt speichert einen Random-Access-Iterator des Typs `RandomIterator`. Es verhält sich wie ein Rand-Access-Iterator, außer bei einer Dereferenzierung. Das Ergebnis von `operator*` wird implizit umgewandelt in `value_type&&:`, um `rvalue reference` zu erhalten.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Die Klassen Vorlage beschreibt ein ausgabeiteratorobjekt. Die Objekte der Klasse `Type` werden in einen Ausgabestream eingefügt, auf den Sie über ein Objekt, das Sie speichert, vom Typ `pointer` auf zugreifen `basic_ostream` \<**Elem**, **Tr**> .|
|[Ostreambuf_iterator-Klasse](../standard-library/ostreambuf-iterator-class.md)|Die Klassen Vorlage beschreibt ein ausgabeiteratorobjekt. Die Elemente der Klasse `Elem` werden in einen ausgabestreampuffer eingefügt, auf den Sie über ein gespeicheres Objekt zugreifen, vom Typ Zeiger auf `basic_streambuf` \<**Elem**, **Tr**> .|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Eine Klasse, die einen Rückgabetyp für eine Funktion bereitstellt `iterator_category` , die einen Ausgabeiterator darstellt|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Eine Klasse, die einen Rückgabetyp für eine Funktion bereitstellt `iterator_category` , die einen Random-Access-Iterator darstellt.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Die Klassen Vorlage beschreibt ein Objekt, das sich wie ein Random-Access-Iterator verhält, nur in umgekehrter Reihenfolge.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Eine Klasse, die auf ein Array mit einem Iterator vom Typ "Random-Access, Unchecked" zugreift. **Hinweis:** Bei dieser Klasse handelt es sich um eine Microsoft-Erweiterung der C++-Standardbibliothek. Der Code, der mit dieser Funktion implementiert wird, ist nicht auf C++-Standardbuildumgebungen übertragbar, die die Microsoft-Erweiterung nicht unterstützen.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)
