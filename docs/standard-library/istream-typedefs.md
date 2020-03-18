---
title: '&lt;iStream&gt;-Typedefs'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425676"
---
# <a name="ltistreamgt-typedefs"></a>&lt;iStream&gt;-Typedefs

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a> iostream

Ein Typ `basic_iostream` spezialisiert auf **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für Klassen Vorlagen [basic_iostream](../standard-library/basic-iostream-class.md), die auf Elemente vom Typ " **char** " mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="istream"></a> istream

Ein Typ `basic_istream` spezialisiert auf **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md), die auf Elemente vom Typ " **char** " mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wiostream"></a> wiostream

Ein Typ `basic_iostream` spezialisiert auf **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für Klassen Vorlagen [basic_iostream](../standard-library/basic-iostream-class.md), die auf Elemente des Typs **wchar_t** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wistream"></a> wistream

Ein Typ `basic_istream` spezialisiert auf **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Hinweise

Der Typ ist ein Synonym für Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md), die auf Elemente des Typs **wchar_t** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="see-also"></a>Siehe auch

[\<istream>](../standard-library/istream.md)
