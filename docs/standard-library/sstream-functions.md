---
title: '&lt;sstream&gt; Funktionen'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: 722cba257b12bb753aaa61ac2f430df76c2ceb93
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560373"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt; Funktionen

||
|-|
|[swap](#sstream_swap)|

## <a name="swap"></a><a name="sstream_swap"></a> Wechsel

Tauscht die Werte zwischen zwei `sstream`-Objekten aus.

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Verweis auf ein `sstream`-Objekt.

*Richting*\
Ein Verweis auf ein `sstream`-Objekt.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion führt `left.swap(right)` aus.

## <a name="see-also"></a>Weitere Informationen

[\<sstream>](../standard-library/sstream.md)
