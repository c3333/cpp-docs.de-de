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
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425184"
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

## <a name="cmatch"></a> cmatch-Typdefinition

Die Typdefinition für „char match_results“.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [match_results-Klasse](../standard-library/match-results-class.md) für Iteratoren des Typs `const char*`.

## <a name="cregex_iterator"></a> cregex_iterator-Typdefinition

Typdefinition für char regex_iterator.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_iterator-Klasse](../standard-library/regex-iterator-class.md) für Iteratoren des Typs `const char*`.

## <a name="cregex_token_iterator"></a> cregex_token_iterator-Typdefinition

Typdefinition für char regex_token_iterator

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md) für Iteratoren des Typs `const char*`.

## <a name="csub_match"></a> csub_match-Typdefinition

Die Typdefinition für „char sub_match“.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [sub_match-Klasse](../standard-library/sub-match-class.md) für Iteratoren des Typs `const char*`.

## <a name="regex"></a> regex-Typdefinition

Die Typdefinition für „char basic_regex“.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [basic_regex Klasse](../standard-library/basic-regex-class.md) für Elemente des Typs **char**.

> [!NOTE]
> High Bit-Zeichen werden bei `regex` unvorhersehbare Ergebnisse haben. Werte außerhalb des Bereichs von 0 bis 127 können zu nicht definiertem Verhalten führen.

## <a name="smatch"></a> smatch-Typdefinition

Die Typdefinition für „string match_results“.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [match_results-Klasse](../standard-library/match-results-class.md) für Iteratoren des Typs `string::const_iterator`.

## <a name="sregex_iterator"></a> sregex_iterator-Typdefinition

Die Typdefinition für „string regex_iterator“.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_iterator-Klasse](../standard-library/regex-iterator-class.md) für Iteratoren des Typs `string::const_iterator`.

## <a name="sregex_token_iterator"></a> sregex_token_iterator-Typdefinition

Typdefinition für string regex_token_iterator.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md) für Iteratoren des Typs `string::const_iterator`.

## <a name="ssub_match"></a> ssub_match-Typdefinition

Die Typdefinition für „string sub_match“.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [sub_match-Klasse](../standard-library/sub-match-class.md) für Iteratoren des Typs `string::const_iterator`.

## <a name="wcmatch"></a> wcmatch-Typdefinition

Die Typdefinition für „wchar match_results“.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [match_results-Klasse](../standard-library/match-results-class.md) für Iteratoren des Typs `const wchar_t*`.

## <a name="wcregex_iterator"></a> wcregex_iterator-Typdefinition

Die Typdefinition für „wchar_t regex_iterator“.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_iterator-Klasse](../standard-library/regex-iterator-class.md) für Iteratoren des Typs `const wchar_t*`.

## <a name="wcregex_token_iterator"></a> wcregex_token_iterator-Typdefinition

Die Typdefinition für „wchar_t regex_token_iterator“.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md) für Iteratoren des Typs `const wchar_t*`.

## <a name="wcsub_match"></a> wcsub_match-Typdefinition

Die Typdefinition für „wchar_t sub_match“.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [sub_match-Klasse](../standard-library/sub-match-class.md) für Iteratoren des Typs `const wchar_t*`.

## <a name="wregex"></a> wregex-Typdefinition

Die Typdefinition für „wchar_t basic_regex“.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [basic_regex-Klasse](../standard-library/basic-regex-class.md) für Elemente des Typs **wchar_t**.

## <a name="wsmatch"></a> wsmatch-Typdefinition

Die Typdefinition für „wstring match_results“.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [match_results-Klasse](../standard-library/match-results-class.md) für Iteratoren des Typs `wstring::const_iterator`.

## <a name="wsregex_iterator"></a> wsregex_iterator-Typdefinition

Die Typdefinition für „wstring regex_iterator“.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_iterator-Klasse](../standard-library/regex-iterator-class.md) für Iteratoren des Typs `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a> wsregex_token_iterator-Typdefinition

Typdefinition für „wstring regex_token_iterator“.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md) für Iteratoren des Typs `wstring::const_iterator`.

## <a name="wssub_match"></a> wssub_match Typdefinition

Die Typdefinition für „wstring sub_match“.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Hinweise

Der Typ beschreibt eine Spezialisierung der Klassen Vorlagen [sub_match-Klasse](../standard-library/sub-match-class.md) für Iteratoren des Typs `wstring::const_iterator`.

## <a name="see-also"></a>Siehe auch

[\<regex>](../standard-library/regex.md)\
[regex_constants-Klasse](../standard-library/regex-constants-class.md)\
[regex_error-Klasse](../standard-library/regex-error-class.md)\
[\<Regex-> Funktionen](../standard-library/regex-functions.md)\
[regex_iterator-Klasse](../standard-library/regex-iterator-class.md)\
[\<Regex-> Operatoren](../standard-library/regex-operators.md)\
[regex_token_iterator-Klasse](../standard-library/regex-token-iterator-class.md)\
[regex_traits-Klasse](../standard-library/regex-traits-class.md)
