---
title: '&lt;string_view &gt; Typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 6aadd4ad3ff08a0b020fd8e683e60063fe516c63
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215594"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view &gt; Typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs beschreibt **`char`** .

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Deklarationen sind gleichwertig:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs beschreibt **`char16_t`** .

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs beschreibt **`char32_t`** .

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs beschreibt **`wchar_t`** .

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Bemerkungen

Die folgenden Deklarationen sind gleichwertig:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Die Größe von **`wchar_t`** beträgt zwei Bytes unter Windows, dies ist jedoch nicht unbedingt der Fall für alle Plattformen. Wenn Sie einen string_view Wide Character Type mit einer Breite benötigen, die auf allen Plattformen garantiert unverändert bleibt, verwenden Sie [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) oder [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Weitere Informationen

[\<string_view>](../standard-library/string-view.md)
