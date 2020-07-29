---
title: char_traits&lt;wchar_t&gt;-Struktur
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 3b2504dbb124ccca7f9b27619585abb2b5795f92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219169"
---
# <a name="char_traitsltwchar_tgt-struct"></a>char_traits&lt;wchar_t&gt;-Struktur

Eine Klasse, die eine Spezialisierung der Vorlagen Struktur ist **, \<CharType> Char_traits** auf ein Element vom Typ **`wchar_t`** .

## <a name="syntax"></a>Syntax

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Bemerkungen

Durch die Spezialisierung kann die Struktur Bibliotheksfunktionen nutzen, die Objekte dieses Typs bearbeiten **`wchar_t`** .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<string>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Char_traits-Struktur](../standard-library/char-traits-struct.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
