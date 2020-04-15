---
title: '&lt;regex&gt;-Typdefinitionen'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 5dbda2df4877da7594dd633e9f203a3780b4adb1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368542"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt;-Typdefinitionen

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch-typedef"></a><a name="cmatch"></a>cmatch Typedef

Die Typdefinition für „char match_results“.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [match_results](../standard-library/match-results-class.md) `const char*`Klasse für Iteratoren vom Typ .

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a>cregex_iterator Typedef

Typdefinition für char regex_iterator.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_iterator](../standard-library/regex-iterator-class.md) `const char*`Klasse für Iteratoren vom Typ .

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a>cregex_token_iterator Typedef

Typdefinition für char regex_token_iterator

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_token_iterator](../standard-library/regex-token-iterator-class.md) `const char*`Klasse für Iteratoren vom Typ .

## <a name="csub_match-typedef"></a><a name="csub_match"></a>csub_match Typedef

Die Typdefinition für „char sub_match“.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [sub_match](../standard-library/sub-match-class.md) `const char*`Klasse für Iteratoren vom Typ .

## <a name="regex-typedef"></a><a name="regex"></a>regex Typedef

Die Typdefinition für „char basic_regex“.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [basic_regex Klasse](../standard-library/basic-regex-class.md) für Elemente vom Typ **char**.

> [!NOTE]
> High Bit-Zeichen werden bei `regex` unvorhersehbare Ergebnisse haben. Werte außerhalb des Bereichs von 0 bis 127 können zu nicht definiertem Verhalten führen.

## <a name="smatch-typedef"></a><a name="smatch"></a>smatch Typedef

Die Typdefinition für „string match_results“.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [match_results](../standard-library/match-results-class.md) `string::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a>sregex_iterator Typedef

Die Typdefinition für „string regex_iterator“.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_iterator](../standard-library/regex-iterator-class.md) `string::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a>sregex_token_iterator Typedef

Typdefinition für string regex_token_iterator.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_token_iterator](../standard-library/regex-token-iterator-class.md) `string::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a>ssub_match Typedef

Die Typdefinition für „string sub_match“.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [sub_match](../standard-library/sub-match-class.md) `string::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a>wcmatch Typedef

Die Typdefinition für „wchar match_results“.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [match_results](../standard-library/match-results-class.md) `const wchar_t*`Klasse für Iteratoren vom Typ .

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a>wcregex_iterator Typedef

Die Typdefinition für „wchar_t regex_iterator“.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_iterator](../standard-library/regex-iterator-class.md) `const wchar_t*`Klasse für Iteratoren vom Typ .

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a>wcregex_token_iterator Typedef

Die Typdefinition für „wchar_t regex_token_iterator“.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_token_iterator](../standard-library/regex-token-iterator-class.md) `const wchar_t*`Klasse für Iteratoren vom Typ .

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a>wcsub_match Typedef

Die Typdefinition für „wchar_t sub_match“.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [sub_match](../standard-library/sub-match-class.md) `const wchar_t*`Klasse für Iteratoren vom Typ .

## <a name="wregex-typedef"></a><a name="wregex"></a>wregex Typedef

Die Typdefinition für „wchar_t basic_regex“.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [basic_regex Klasse](../standard-library/basic-regex-class.md) für Elemente vom Typ **wchar_t**.

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a>wsmatch Typedef

Die Typdefinition für „wstring match_results“.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [match_results](../standard-library/match-results-class.md) `wstring::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a>wsregex_iterator Typedef

Die Typdefinition für „wstring regex_iterator“.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_iterator](../standard-library/regex-iterator-class.md) `wstring::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a>wsregex_token_iterator Typedef

Typdefinition für „wstring regex_token_iterator“.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [regex_token_iterator](../standard-library/regex-token-iterator-class.md) `wstring::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a>wssub_match Typedef

Die Typdefinition für „wstring sub_match“.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Bemerkungen

Der Typ beschreibt eine Spezialisierung der Klassenvorlage [sub_match](../standard-library/sub-match-class.md) `wstring::const_iterator`Klasse für Iteratoren vom Typ .

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_constants-Klasse](../standard-library/regex-constants-class.md)\
[regex_error-Klasse](../standard-library/regex-error-class.md)\
[\<regex> Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<regex> Operatoren](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)
