---
title: '&lt;string&gt;-Typdefinitionen'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 083209f0121ac38d8adf81975577257e4e23a393
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845431"
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt;-Typdefinitionen

[Schnür](#string)\
[u16string](#u16string)\
[u32string](#u32string)\
[wstring](#wstring)

## <a name="string"></a><a name="string"></a>-Zeichenfolge

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string](../standard-library/basic-string-class.md) mit Elementen des Typs beschreibt **`char`** .

Andere `basic_string` spezialisierende Typdefinitionen umfassen [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string) und [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Deklarationen sind gleichwertig:

```cpp
string str("");

basic_string<char> str("");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a><a name="u16string"></a> u16string

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string](../standard-library/basic-string-class.md) mit Elementen des Typs beschreibt **`char16_t`** .

Andere `basic_string` spezialisierende Typdefinitionen umfassen [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string) und [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a><a name="u32string"></a> u32string

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string](../standard-library/basic-string-class.md) mit Elementen des Typs beschreibt **`char32_t`** .

Andere `basic_string` spezialisierende Typdefinitionen umfassen [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) und [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a><a name="wstring"></a> wstring

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string](../standard-library/basic-string-class.md) mit Elementen des Typs beschreibt **`wchar_t`** .

Andere `basic_string` spezialisierende Typdefinitionen umfassen [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) und [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Deklarationen sind gleichwertig:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Die Größe von **`wchar_t`** ist Implementierungs definiert. Wenn Ihr Code davon abhängt **`wchar_t`** , dass er eine bestimmte Größe hat, überprüfen Sie die Implementierung Ihrer Plattform (z `sizeof(wchar_t)` . b. mit). Wenn Sie einen Zeichenfolgentyp mit einer Breite benötigen, die auf allen Plattformen garantiert dieselbe ist, verwenden Sie [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) oder [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Weitere Informationen

[\<string>](../standard-library/string.md)
