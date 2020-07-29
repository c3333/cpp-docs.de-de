---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 68b1865fd9c45c3782917edba273083dac086548
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212123"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definiert die Containerklassen Vorlage `basic_string` und verschiedene unterstützende Vorlagen.

Weitere Informationen zu `basic_string` finden Sie unter [basic_string-Klasse](../standard-library/basic-string-class.md).

## <a name="syntax"></a>Syntax

```cpp
#include <string>
```

## <a name="remarks"></a>Bemerkungen

Die Programmiersprache C++ und die C++-Standardbibliothek unterstützen zwei Arten von Zeichenfolgen:

- Auf NULL endende Zeichenarrays werden häufig als C-Zeichenfolgen bezeichnet.

- Klassen Vorlagen Objekte des Typs, `basic_string` die alle **`char`** -ähnlichen Vorlagen Argumente verarbeiten.

### <a name="typedefs"></a>TypeDefs

|Typname|Beschreibung|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Ein Typ, der eine Spezialisierung der Klassen Vorlage `basic_string` mit Elementen des Typs **`char`** als beschreibt `string` .|
|[wstring](../standard-library/string-typedefs.md#wstring)|Ein Typ, der eine Spezialisierung der Klassen Vorlage `basic_string` mit Elementen des Typs **`wchar_t`** als beschreibt `wstring` .|
|[u16string](../standard-library/string-typedefs.md#u16string)|Ein Typ, der eine Spezialisierung der Klassen Vorlage auf `basic_string` der Grundlage von Elementen des Typs beschreibt **`char16_t`** .|
|[u32string](../standard-library/string-typedefs.md#u32string)|Ein Typ, der eine Spezialisierung der Klassen Vorlage auf `basic_string` der Grundlage von Elementen des Typs beschreibt **`char32_t`** .|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator +](../standard-library/string-operators.md#op_add)|Verkettet zwei Zeichenfolgenobjekte.|
|[Operator! =](../standard-library/string-operators.md#op_neq)|Testet, ob das Zeichenfolgenobjekt links vom Operator ungleich dem Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator = =](../standard-library/string-operators.md#op_eq_eq)|Testet, ob das Zeichenfolgenobjekt links vom Operator gleich dem Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator<](../standard-library/string-operators.md#op_lt)|Testet, ob das Zeichenfolgenobjekt links vom Operator kleiner als das Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator<=](../standard-library/string-operators.md#op_lt_eq)|Testet, ob das Zeichenfolgenobjekt links vom Operator kleiner als oder gleich dem Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator<\<](../standard-library/string-operators.md#op_lt_lt)|Eine Vorlagenfunktion, die eine Zeichenfolge in den Ausgabestream einfügt.|
|[Operator>](../standard-library/string-operators.md#op_gt)|Testet, ob das Zeichenfolgenobjekt links vom Operator größer als das Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator>=](../standard-library/string-operators.md#op_gt_eq)|Testet, ob das Zeichenfolgenobjekt links vom Operator größer als oder gleich dem Zeichenfolgenobjekt rechts vom Operator ist.|
|[Operator>>](../standard-library/string-operators.md#op_gt_gt)|Eine Vorlagenfunktion, die eine Zeichenfolge aus dem Eingabestream extrahiert.|

### <a name="specialized-template-functions"></a>Spezialisierte Vorlagenfunktionen

|||
|-|-|
|hash|Erzeugt einen Hashwert einer Zeichenfolge.|
|[swap](../standard-library/string-functions.md#swap)|Tauscht die Arrays von Zeichen für zwei Zeichenfolgen aus.|
|[Stod](../standard-library/string-functions.md#stod)|Konvertiert eine Zeichenfolge in eine **`double`** .|
|[Stof](../standard-library/string-functions.md#stof)|Konvertiert eine Zeichenfolge in eine **`float`** .|
|[Stoi](../standard-library/string-functions.md#stoi)|Konvertiert eine Zeichenfolge in eine Ganzzahl.|
|[stold](../standard-library/string-functions.md#stold)|Konvertiert eine Zeichenfolge in eine **`long double`** .|
|[stoll](../standard-library/string-functions.md#stoll)|Konvertiert eine Zeichenfolge in eine **`long long`** .|
|[Stoul](../standard-library/string-functions.md#stoul)|Konvertiert eine Zeichenfolge in eine **`unsigned long`** .|
|[stoull](../standard-library/string-functions.md#stoull)|Konvertiert eine Zeichenfolge in eine **`unsigned long long`** .|
|[to_string](../standard-library/string-functions.md#to_string)|Konvertiert einen Wert in einen `string`-Wert.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Konvertiert einen Wert in eine breite `string`.|

### <a name="functions"></a>Functions

|Funktion|BESCHREIBUNG|
|-|-|
|[getline-Vorlage](../standard-library/string-functions.md#getline)|Extrahiert Zeichenfolgen aus dem Eingabestream zeilenweise.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[Basic_string-Klasse](../standard-library/basic-string-class.md)|Eine Klassen Vorlage, die Objekte beschreibt, die eine Sequenz beliebiger Zeichen ähnlicher Objekte speichern können.|
|[Char_traits-Struktur](../standard-library/char-traits-struct.md)|Eine Klassen Vorlage, die Attribute beschreibt, die einem Zeichen vom Typ "CharType" zugeordnet sind.|

### <a name="specializations"></a>Spezialisierungen

|||
|-|-|
|[Char_traits- \<char> Struktur](../standard-library/char-traits-char-struct.md)|Eine Struktur, die eine Spezialisierung der Vorlagen Struktur `char_traits` \<CharType> zu einem Element vom Typ ist **`char`** .|
|[Char_traits<wchar_t> Struktur](../standard-library/char-traits-wchar-t-struct.md)|Eine Struktur, die eine Spezialisierung der Vorlagen Struktur `char_traits` \<CharType> zu einem Element vom Typ ist **`wchar_t`** .|
|[Char_traits<char16_t> Struktur](../standard-library/char-traits-char16-t-struct.md)|Eine Struktur, die eine Spezialisierung der Vorlagen Struktur `char_traits` \<CharType> zu einem Element vom Typ ist **`char16_t`** .|
|[Char_traits<char32_t> Struktur](../standard-library/char-traits-char32-t-struct.md)|Eine Struktur, die eine Spezialisierung der Vorlagen Struktur `char_traits` \<CharType> zu einem Element vom Typ ist **`char32_t`** .|

## <a name="requirements"></a>Requirements (Anforderungen)

- **Header:**\<string>

- **Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
