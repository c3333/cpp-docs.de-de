---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 1beade28ceec0f1552def4bc70c2e95e6b2aa24d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215438"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

Definiert Typen, Funktionen und Operatoren einer C++-Standardbibliothek, mit denen Paare von Objekten erstellt und verwaltet werden können. Solche Paare von Objekten sind immer dann nützlich, wenn zwei Objekte so behandelt werden müssen, als wären sie ein Objekt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<utility>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

Paare werden häufig in der C++-Standardbibliothek verwendet. Sie sind sowohl als Argumente als auch als Rückgabewerte für verschiedene Funktionen sowie als Elementtypen für Container wie [map-Klasse](../standard-library/map-class.md) und [multimap-Klasse](../standard-library/multimap-class.md) erforderlich. Der- \<utility> Header wird automatisch von eingeschlossen \<map> , um die Verwaltung der Schlüssel-Wert-Paar-Typelemente zu unterstützen.

> [!NOTE]
> Der- \<utility> Header verwendet die-Anweisung `#include <initializer_list>` . Er bezieht sich auch auf, `class tuple` wie in definiert \<tuple> .

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|type|BESCHREIBUNG|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Gleit Komma Format für die primitive numerische Konvertierung.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Eine Klasse, die den Typ eines `pair`-Elements umschließt.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Eine Klasse, die eine `pair`-Elementanzahl umschließt.|

### <a name="objects"></a>Objekte

|Vorlage|Beschreibung|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|Eine Alias Vorlage, die für den allgemeinen Fall definiert ist, in dem `T``std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|Hilfsalias Vorlage zum Konvertieren beliebiger Typparameter Pakete in eine Index Sequenz gleicher Länge|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| Hilfsalias Vorlage zum Vereinfachen der Erstellung eines `std::index_sequence` Typs. |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|Hilfsalias Vorlage zum Vereinfachen der Erstellung eines `std::integer_sequence` Typs.|

### <a name="functions"></a>Functions

|Funktion|BESCHREIBUNG|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Gibt den Typ zurück.|
|[declval](../standard-library/utility-functions.md#declval)|Kurzform Ausdrucks Auswertung.|
|[Schlag](../standard-library/utility-functions.md#exchange)|Weist einem Objekt einen neuen Wert zu und gibt den alten Wert zurück.|
|[vorgezogen](../standard-library/utility-functions.md#forward)|Verhindert durch perfektes Weiterleiten, dass der Referenztyp (entweder `lvalue` oder `rvalue`) des Arguments verdeckt wird.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Eine Funktion, die ein Element aus einem `pair`-Objekt abruft.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Eine Vorlagenhilfsfunktion, die zum Erstellen von Objekten des Typs `pair` verwendet wird, wobei die Komponententypen auf den Datentypen basieren, die als Parameter übergeben werden.|
|[move](../standard-library/utility-functions.md#move)|Gibt das als Eingabe übergebene Argument als einen `rvalue`-Verweis zurück.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Tauscht die Elemente zweier `pair`-Objekte.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Konvertiert einen Wert in eine Zeichenfolge.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator! =](../standard-library/utility-operators.md#op_neq)|Testet, ob das pair-Objekt links vom Operator ungleich dem pair-Objekt rechts vom Operator ist.|
|[Operator = =](../standard-library/utility-operators.md#op_eq_eq)|Testet, ob das pair-Objekt links vom Operator gleich dem pair-Objekt rechts vom Operator ist.|
|[KOM\<](../standard-library/utility-operators.md#op_lt)|Testet, ob das pair-Objekt links vom Operator kleiner als das pair-Objekt rechts vom Operator ist.|
|[KOM\<=](../standard-library/utility-operators.md#op_gt_eq)|Testet, ob das pair-Objekt links vom Operator kleiner gleich dem pair-Objekt rechts vom Operator ist.|
|[Operator>](../standard-library/utility-operators.md#op_gt)|Testet, ob das pair-Objekt links vom Operator größer als das pair-Objekt rechts vom Operator ist.|
|[Operator>=](../standard-library/utility-operators.md#op_gt_eq)|Testet, ob das pair-Objekt links vom Operator größer gleich dem pair-Objekt rechts vom Operator ist.|

### <a name="structs"></a>Strukturen

|Struktur|BESCHREIBUNG|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Eine für verwendete Struktur `from_chars` .|
|[Identität](../standard-library/identity-structure.md)|Eine Struktur, die eine Typdefinition als den Vorlagenparameter bereitstellt.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Umfasst auch Strukturen `in_place_type_t` und `in_place_index_t` .|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Stellt eine Ganzzahlsequenz dar.|
|[Pär](../standard-library/pair-structure.md)|Ein Typ, der die Möglichkeit bietet, zwei Objekte als ein einzelnes Objekt zu behandeln.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Ein Typ, der verwendet wird, um den separaten Konstruktor und die Funktions Überladung beizubehalten.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Eine für verwendete Struktur `to_chars` .|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
