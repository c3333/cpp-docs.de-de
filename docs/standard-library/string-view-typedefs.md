---
title: '&lt;string_view&gt; Typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427578"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; Typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a>string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage beschreibt [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Hinweise

Die folgenden Deklarationen sind gleichwertig:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a>u16string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage beschreibt [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Hinweise

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a>u32string_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage beschreibt [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Hinweise

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>wstring_view

Ein Typ, der eine Spezialisierung der Klassen Vorlage beschreibt [basic_string_view](../standard-library/basic-string-view-class.md) mit Elementen des Typs **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Hinweise

Die folgenden Deklarationen sind gleichwertig:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Eine Liste der String-Konstruktoren finden Sie unter [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> Die Größe der **wchar_t** beträgt zwei Bytes unter Windows, aber dies ist nicht unbedingt der Fall für alle Plattformen. Wenn Sie einen string_view Wide Character Type mit einer Breite benötigen, die auf allen Plattformen garantiert unverändert bleibt, verwenden Sie [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) oder [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Siehe auch

[\<string_view >](../standard-library/string-view.md)
