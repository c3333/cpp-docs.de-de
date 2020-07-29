---
title: '&lt;regex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 9d7f84ac47979cf398ae1f94e4d01ba0915da299
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217531"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

Definiert eine Klassen Vorlage zum Analysieren [regulärer Ausdrücke (C++)](../standard-library/regular-expressions-cpp.md)und mehrerer Klassen Vorlagen und Funktionen, um Text nach Übereinstimmungen mit einem Objekt für reguläre Ausdrücke zu suchen.

## <a name="syntax"></a>Syntax

```cpp
#include <regex>
```

## <a name="remarks"></a>Bemerkungen

Um ein Objekt für einen regulären Ausdruck zu erstellen, verwenden Sie die Klassen Vorlage [basic_regex Klasse](../standard-library/basic-regex-class.md) oder eine der zugehörigen Spezialisierungs-, [Regex](../standard-library/regex-typedefs.md#regex) -und [wregex](../standard-library/regex-typedefs.md#wregex)-Elemente sowie die Syntax Flags des Typs [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

Um Text nach Übereinstimmungen mit einem Objekt für reguläre Ausdrücke zu suchen, verwenden Sie die Vorlagen Funktionen [regex_match](../standard-library/regex-functions.md#regex_match) und [regex_search](../standard-library/regex-functions.md#regex_search)zusammen mit den übereinstimmungsflags des Typs [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type). Diese Funktionen geben Ergebnisse zurück, indem Sie die Klassen Vorlage [match_results Klasse](../standard-library/match-results-class.md) und ihre Spezialisierungs-, [cmatch](../standard-library/regex-typedefs.md#cmatch)-, [wcmatch](../standard-library/regex-typedefs.md#wcmatch)-, [smatch](../standard-library/regex-typedefs.md#smatch)-und [wsmatch](../standard-library/regex-typedefs.md#wsmatch)-Klassen zusammen mit der Klassen Vorlage [sub_match Klasse](../standard-library/sub-match-class.md) und den zugehörigen Spezialisierungs-, [csub_match](../standard-library/regex-typedefs.md#csub_match)-, [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)-, [ssub_match](../standard-library/regex-typedefs.md#ssub_match)und [wssub_match](../standard-library/regex-typedefs.md#wssub_match)verwenden.

Um Text zu ersetzen, der mit einem Objekt für reguläre Ausdrücke übereinstimmt, verwenden Sie die Vorlagen Funktion [regex_replace](../standard-library/regex-functions.md#regex_replace)zusammen mit den übereinstimmungsflags des Typs [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Um mehrere Übereinstimmungen eines Objekts für reguläre Ausdrücke zu durchlaufen, verwenden Sie die Klassen Vorlagen [regex_iterator Klasse](../standard-library/regex-iterator-class.md) und [regex_token_iterator Klasse](../standard-library/regex-token-iterator-class.md) oder eine ihrer Spezialisierungs-, [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)-, [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)-, [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)-, [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator) [-, cregex_token_iterator-, sregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator) [-, wcregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)- [, wsregex_token_iterator-](../standard-library/regex-typedefs.md#wcregex_token_iterator)oder [regex_constants](../standard-library/regex-typedefs.md#wsregex_token_iterator), zusammen mit den übereinstimmungsflags des Typs [match_flag_type::](../standard-library/regex-constants-class.md#match_flag_type).

Um die Details der Grammatik regulärer Ausdrücke zu ändern, schreiben Sie eine Klasse, in der die Merkmale des regulären Ausdrucks implementiert sind.

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Umschließt einen regulären Ausdruck.|
|[match_results](../standard-library/match-results-class.md)|Enthält eine Sequenz von Teilübereinstimmungen.|
|[regex_constants](../standard-library/regex-constants-class.md)|Enthält zusammengestellte Konstanten.|
|[regex_error](../standard-library/regex-error-class.md)|Meldet einen ungültigen regulären Ausdruck.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Durchläuft Übereinstimmungsergebnisse.|
|[regex_traits](../standard-library/regex-traits-class.md)|Beschreibt die Merkmale von Elementen zum Abgleichen.|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|Beschreibt die Merkmale von für den Abgleich **`char`** .|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|Beschreibt die Merkmale von für den Abgleich **`wchar_t`** .|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Durchläuft Teilübereinstimmungen.|
|[sub_match](../standard-library/sub-match-class.md)|Beschreibt eine Teilübereinstimmung.|

### <a name="type-definitions"></a>Typdefinitionen

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Typdefinition für **`char`** `match_results` .|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Typdefinition für **`char`** `regex_iterator` .|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Typdefinition für **`char`** `regex_token_iterator` .|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Typdefinition für **`char`** `sub_match` .|
|[regex](../standard-library/regex-typedefs.md#regex)|Typdefinition für **`char`** `basic_regex` .|
|[smatch](../standard-library/regex-typedefs.md#smatch)|Typdefinition für `string` `match_results`.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Typdefinition für `string` `regex_iterator`.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Typdefinition für `string` `regex_token_iterator`.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Typdefinition für `string` `sub_match`.|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Typdefinition für **`wchar_t`** `match_results` .|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Typdefinition für **`wchar_t`** `regex_iterator` .|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Typdefinition für **`wchar_t`** `regex_token_iterator` .|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Typdefinition für **`wchar_t`** `sub_match` .|
|[wregex](../standard-library/regex-typedefs.md#wregex)|Typdefinition für **`wchar_t`** `basic_regex` .|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Typdefinition für `wstring` `match_results`.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Typdefinition für `wstring` `regex_iterator`.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Typdefinition für `wstring` `regex_token_iterator`.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Typdefinition für `wstring` `sub_match`.|

### <a name="functions"></a>Functions

|Funktion|BESCHREIBUNG|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Gleicht einen regulären Ausdruck exakt ab.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Ersetzt übereinstimmende reguläre Ausdrücke.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Sucht nach einer Übereinstimmung mit einem regulären Ausdruck.|
|[swap](../standard-library/regex-functions.md#swap)|Tauscht `basic_regex`- oder `match_results`-Objekte.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator = =](../standard-library/regex-operators.md#op_eq_eq)|Vergleich von verschiedenen Objekten: gleich.|
|[Operator! =](../standard-library/regex-operators.md#op_neq)|Vergleich von verschiedenen Objekten: ungleich.|
|[Operator<](../standard-library/regex-operators.md#op_lt)|Vergleich von verschiedenen Objekten: kleiner als.|
|[KOM\<=](../standard-library/regex-operators.md#op_gt_eq)|Vergleich von verschiedenen Objekten: kleiner als oder gleich.|
|[Operator>](../standard-library/regex-operators.md#op_gt)|Vergleich von verschiedenen Objekten: größer als.|
|[Operator>=](../standard-library/regex-operators.md#op_gt_eq)|Vergleich von verschiedenen Objekten: größer als oder gleich.|
|[Operator<<](../standard-library/regex-operators.md#op_lt_lt)|Fügt ein `sub_match`-Objekt in einem Stream ein.|

## <a name="see-also"></a>Weitere Informationen

[Reguläre Ausdrücke (C++)](../standard-library/regular-expressions-cpp.md)\
[regex_constants-Klasse](../standard-library/regex-constants-class.md)\
[regex_error-Klasse](../standard-library/regex-error-class.md)\
[\<regex>Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<regex>Veranstalter](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)\
[\<regex>Typedefs](../standard-library/regex-typedefs.md)
