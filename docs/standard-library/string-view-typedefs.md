---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 0ec278484b7c1c9887771f6cbe7e5d0b05205dd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376678"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

Ein Typ, der eine Spezialisierung der Klassenvorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen vom Typ **char**beschreibt.

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

Ein Typ, der eine Spezialisierung [basic_string_view](../standard-library/basic-string-view-class.md) der Klassenvorlage `char16_t`basic_string_view mit Elementen vom Typ beschreibt.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

Ein Typ, der eine Spezialisierung [basic_string_view](../standard-library/basic-string-view-class.md) der Klassenvorlage `char32_t`basic_string_view mit Elementen vom Typ beschreibt.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

Ein Typ, der eine Spezialisierung der Klassenvorlage [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen vom Typ **wchar_t**beschreibt.

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
> Die Größe von **wchar_t** beträgt zwei Bytes unter Windows, aber dies ist nicht unbedingt für alle Plattformen der Fall. Wenn Sie einen string_view breiten Zeichentyp mit einer Breite benötigen, die auf allen Plattformen garantiert gleich bleibt, verwenden Sie [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) oder [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Siehe auch

[\<string_view>](../standard-library/string-view.md)
