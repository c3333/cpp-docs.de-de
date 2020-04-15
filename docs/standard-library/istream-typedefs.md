---
title: '&lt;iStream&gt;-Typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: e9228bddcc3b99503b6b5f0e93b5ed6eeed773d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363083"
---
# <a name="ltistreamgt-typedefs"></a>&lt;iStream&gt;-Typedefs

||||
|-|-|-|
|[Iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a><a name="iostream"></a>Iostream

Ein `basic_iostream` Typ, der auf **char**spezialisiert ist.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_iostream](../standard-library/basic-iostream-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="istream"></a><a name="istream"></a>Istream

Ein `basic_istream` Typ, der auf **char**spezialisiert ist.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_istream](../standard-library/basic-istream-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="wiostream"></a><a name="wiostream"></a>wiostream

Ein `basic_iostream` Typ, der auf **wchar_t**spezialisiert ist.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_iostream](../standard-library/basic-iostream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="wistream"></a><a name="wistream"></a>wistream

Ein `basic_istream` Typ, der auf **wchar_t**spezialisiert ist.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_istream](../standard-library/basic-istream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="see-also"></a>Siehe auch

[\<istream>](../standard-library/istream.md)
