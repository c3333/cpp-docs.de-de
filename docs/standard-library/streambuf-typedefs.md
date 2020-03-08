---
title: '&lt;streambuf&gt;-Typdefinition'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866211"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;-Typdefinition

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a> streambuf

Eine Spezialisierung von `basic_streambuf`, die **char** als Vorlagen Parameter verwendet.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für die Klassen Vorlage [basic_streambuf](../standard-library/basic-streambuf-class.md), die auf Elemente vom Typ " **char** " mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wstreambuf"></a> wstreambuf

Eine Spezialisierung der `basic_streambuf`, die **wchar_t** als Vorlagen Parameter verwendet.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für die Klassen Vorlage [basic_streambuf](../standard-library/basic-streambuf-class.md), die auf Elemente des Typs **wchar_t** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="see-also"></a>Weitere Informationen

[\<streambuf>](../standard-library/streambuf.md)
