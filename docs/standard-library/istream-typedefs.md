---
title: '&lt;iStream&gt;-Typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: c66a4349a016eb8428a8aa8eb260a78b4bac9efb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846471"
---
# <a name="ltistreamgt-typedefs"></a>&lt;iStream&gt;-Typedefs

[iostream](#iostream)\
[IStream](#istream)\
[wiostream](#wiostream)\
[wistream](#wistream)

## <a name="iostream"></a><a name="iostream"></a> iostream

Ein Typ, `basic_iostream` der auf spezialisiert ist **`char`** .

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_iostream](../standard-library/basic-iostream-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="istream"></a><a name="istream"></a> IStream

Ein Typ, `basic_istream` der auf spezialisiert ist **`char`** .

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wiostream"></a><a name="wiostream"></a> wiostream

Ein Typ, `basic_iostream` der auf spezialisiert ist **`wchar_t`** .

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_iostream](../standard-library/basic-iostream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wistream"></a><a name="wistream"></a> wistream

Ein Typ, `basic_istream` der auf spezialisiert ist **`wchar_t`** .

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="see-also"></a>Weitere Informationen

[\<istream>](../standard-library/istream.md)
