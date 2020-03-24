---
title: Hash&lt;string_view&gt; Spezialisierung
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::hash
helpviewer_keywords:
- std::basic_string_view::hash
ms.openlocfilehash: c7bddd5fcf9008b958854fd4d7b72ea2e94cba47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214954"
---
# <a name="hashltstring_viewgt-specialization"></a>Hash&lt;string_view&gt; Spezialisierung

Eine Vorlagen Spezialisierung, die einen Hashwert erstellt, wenn ein string_view angegeben wird.

```cpp
template <class CharType, class Traits>
struct hash<basic_string_view<CharType, Traits>>
{
    typedef basic_string_view<CharType, Traits> argument_type;
    typedef size_t result_type;

    size_t operator()(const basic_string_view<CharType, Traits>) const
        noexcept;
};
```

### <a name="remarks"></a>Bemerkungen

Der Hash einer string_view der dem Hash des zugrunde liegenden Zeichen folgen Objekts gleicht.

### <a name="example"></a>Beispiel

```cpp
//compile with: /std:c++17
#include <string>
#include <string_view>
#include <iostream>

using namespace std;

int main()
{
    string_view sv{ "Hello world" };
    string s{ "Hello world" };
    cout << boolalpha << (hash<string_view>{}(sv)
        == hash<string>{}(s)); // true
}
```
