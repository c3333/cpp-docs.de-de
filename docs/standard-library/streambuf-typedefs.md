---
title: '&lt;streambuf&gt;-Typdefinition'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376685"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt;-Typdefinition

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

Eine Spezialisierung `basic_streambuf` davon verwendet **char** als Vorlagenparameter.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für die Klassenvorlage [basic_streambuf](../standard-library/basic-streambuf-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

Eine Spezialisierung `basic_streambuf` davon verwendet **wchar_t** als Vorlagenparameter.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für die Klassenvorlage [basic_streambuf](../standard-library/basic-streambuf-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="see-also"></a>Siehe auch

[\<streambuf>](../standard-library/streambuf.md)
