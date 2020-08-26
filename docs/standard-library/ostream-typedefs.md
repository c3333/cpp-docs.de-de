---
title: '&lt;ostream&gt;-Typdefinitionen'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: ff9f19f56c8d8fdb9e469e6361a5419468fe7e67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846406"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;-Typdefinitionen

[ostream](#ostream)\
[wostream](#wostream)

## <a name="ostream"></a><a name="ostream"></a> ostream

Erstellt einen Typ aus Basic_ostream, der spezialisiert ist **`char`** und auf `char_traits` spezialisiert ist **`char`** .

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ostream](../standard-library/basic-ostream-class.md), das auf Elemente des Typs **`char`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="wostream"></a><a name="wostream"></a> wostream

Erstellt einen Typ aus Basic_ostream, der spezialisiert ist **`wchar_t`** und auf `char_traits` spezialisiert ist **`wchar_t`** .

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassen Vorlagen [basic_ostream](../standard-library/basic-ostream-class.md), das auf Elemente des Typs **`wchar_t`** mit Standard Zeichen Merkmalen spezialisiert ist.

## <a name="see-also"></a>Weitere Informationen

[\<ostream>](../standard-library/ostream.md)
