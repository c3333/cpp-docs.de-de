---
title: '&lt;ostream&gt;-Typdefinitionen'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373584"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt;-Typdefinitionen

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>Ostream

Erstellt einen Typ aus basic_ostream, `char_traits` der auf **char** und auf **char**spezialisiert ist.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ostream](../standard-library/basic-ostream-class.md), spezialisiert auf Elemente vom Typ **char** mit Standardzeichenmerkmalen.

## <a name="wostream"></a><a name="wostream"></a>wostream

Erstellt einen Typ aus basic_ostream, `char_traits` der auf **wchar_t** spezialisiert ist und auf **wchar_t**spezialisiert ist.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Bemerkungen

Der Typ ist ein Synonym für Klassenvorlage [basic_ostream](../standard-library/basic-ostream-class.md), spezialisiert auf Elemente vom Typ **wchar_t** mit Standardzeichenmerkmalen.

## <a name="see-also"></a>Siehe auch

[\<ostream>](../standard-library/ostream.md)
